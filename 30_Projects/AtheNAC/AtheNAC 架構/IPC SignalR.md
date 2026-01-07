# PIXIS ProbePortWorker 與 CoreServiceWorker 通訊架構分析

> **文件日期**: 2026-01-07

---

## 1. 系統元件概覽

| 元件 | 位置 | 角色 |
| :--- | :--- | :--- |
| **CoreServiceWorker** | Server 端 | 中央管理服務 |
| **ProbeDaemonWorker** | Probe 硬體 | 本機代理/中繼站 |
| **ProbePortWorker** | Probe 硬體 (可能為 Container) | 實際執行 NAC 任務 |

---

## 2. 通訊架構總覽

```
┌─ 同一台 Probe 機器 ─────────────────────────────────────────┐
│                                                            │
│  PortWorker ──Unix Socket──> ProbeDaemon ── SignalR ───────┼─> CoreService
│     │                            │                         │      (遠端)
│     │                            │                         │
│   無網路                      需要網路                       │
│   存取權                      (outbound)                    │
│                                                            │
└────────────────────────────────────────────────────────────┘
          │
          │ 這台機器的網卡可能在隔離 VLAN
          │ PortWorker 和 Daemon 的通訊
          │ 不經過網路，只經過本機檔案
```

## 3. MessageSender.cs 的兩種通訊方式

`PIXIS.ProbePortWorker.Service.MessageSender` 提供兩種通訊管道：

### 3.1 SignalR 路徑 (ProxyToCoreService)

``` txt
ProbePortWorker
      │
      │ MessageSender.Send()
      │ 呼叫 ProbeDaemonConnection.ProxyToCoreService()
      ▼
┌─────────────────────────────────────────────────────────────┐
│ DaemonSocketProxyServer (YARP)                              │
│ 監聽 localhost:TCP → 轉發到 Unix Domain Socket               │
└─────────────────────────────────────────────────────────────┘
      │
      │ Unix Domain Socket (/var/run/pixis/*.sock)
      ▼
ProbeDaemonWorker (PortWorkerHub.ProxyToCoreService)
      │
      │ CoreServiceConnection.ProxyPortWorkerMessage()
      │ SignalR WebSocket
      ▼
CoreServiceWorker (ProbeDaemonHub.ProxyPortWorkerMessage)
```
**特點：**

- 所有連線皆為 Outbound
    
- PortWorker 不需對外開放 Port
    
- 透過 Daemon 中繼，具備離線暫存能力

### 3.2 HTTP 路徑 (PostToServer / PostAsContentAsync)


```txt
ProbePortWorker
      │
      │ MessageSender.PostToServer()
      │ 直接 HTTP 請求
      ▼
	CoreServiceWorker (/PortWorkerReport)
```
**特點：**

- 直接 HTTP 連線到 Server
    
- 有同步回應 (ResultMessage)
    
- 需要 PortWorker 有對外網路存取能力
    

---

## 4. ProbeDaemon 的角色 - 智慧代理

ProbeDaemon 不只是透明代理，還具備額外功能：

| **功能**     | **說明**                               |
| ---------- | ------------------------------------ |
| **訊息轉發**   | 將 PortWorker 訊息轉發到 CoreService       |
| **附加識別資訊** | 從 PortNumber 查詢並附加 PixisProbeId      |
| **離線暫存**   | CoreService 斷線時，暫存 DHCP 相關事件到 LiteDB |
| **連線狀態管理** | 只有連線時才轉發，否則做離線處理                     |
### 離線處理邏輯 (PortWorkerHub.cs)
``` c#
if (csConnection.State == HubConnectionState.Connected)
{
    await csConnection.ProxyPortWorkerMessage(pixisProbeId, evt);
}
else
{
    // 特定事件暫存到本地 LiteDB
    switch (evt.ActionCode)
    {
        case ActionCode.AssignDhcpV4IP:
        case ActionCode.AssignDhcpV6IP:
        case ActionCode.ReleaseDhcp:
            localDBService.StorePortWorkerEvent(pixisProbeId, ...);
            break;
    }
}
```

## 5. Unix Domain Socket 機制

### 5.1 什麼是 Unix Domain Socket？

Unix Domain Socket 是**本機檔案系統上的 IPC (Inter-Process Communication) 機制**，不經過網路協定棧。

| **特性** | **說明**              |
| ------ | ------------------- |
| 通訊媒介   | 檔案系統中的 socket 檔案    |
| 網路需求   | **不需要網路**，純本機通訊     |
| 存取控制   | 檔案系統權限 (rwx)        |
| 效能     | 比 TCP localhost 更高效 |

### 5.2 架構中的實作

**ProbeDaemonWorker 監聽 Socket：**

```C#
// Program.cs
kestrelOption.ListenUnixSocket(socketPath);
// socketPath = /var/run/pixis/{name}.sock
```

**ProbePortWorker 透過 YARP 連接：**

```C#
// DaemonSocketProxyServer.cs
var sock = new Socket(AddressFamily.Unix, SocketType.Stream, ProtocolType.Unspecified);
await sock.ConnectAsync(
    new UnixDomainSocketEndPoint(configuration.GetPortWorkerSetting().GetFullDaemonSocketName()),
    ct
);
```

### 5.3 為什麼需要 YARP Proxy？

SignalR Client 不原生支援 Unix Domain Socket，因此使用 YARP 作為本地代理：

```txt
SignalR Client → localhost:TCP → YARP Proxy → Unix Socket → Daemon Kestrel
```

## 6. 現有架構的安全問題

### 6.1 Legacy HTTP 直連問題

`PortWorkerRequestService.SendLegacyRequest()` 讓 CoreService 直接 HTTP 連到 PortWorker：

```C#
IPEndPoint targetEndPoint = GetIpEndPoint(portWorker.CommunicationIP, PixisBindingPort.PortWorkerPort);
// 直接連到 http://{PortWorker IP}:18001/Command
```

| **問題**      | **影響**                       |
| ----------- | ---------------------------- |
| **攻擊面增加**   | 每個 PortWorker 都暴露 Port 18001 |
| **防火牆配置複雜** | 需為每個 PortWorker IP 設定入站規則    |
| **網路隔離破壞**  | Server 需要能路由到每個 PortWorker   |
| **VLAN 限制** | 隔離 VLAN 中的 PortWorker 無法被連入  |

## 7. 建議改進方向

### 7.1 全面採用 Daemon 代理模式

將所有 CoreService → PortWorker 的通訊都透過 Daemon 中繼：
```txt
目前 (Legacy):
  CoreService ──HTTP──> PortWorker (需開 Port)

建議:
  CoreService ──SignalR──> Daemon ──Unix Socket──> PortWorker
                (已建立連線)    (本機通訊)
```

### 7.2 需要變更的程式碼

1. **移除或重構** `PortWorkerRequestService.SendLegacyRequest()`
    
2. **新增** Daemon 到 PortWorker 的反向通訊介面
    
3. **更新** `IDaemonToPortWorkerRequest` 加入命令傳遞方法


## 附錄：關鍵程式碼位置

|**檔案**|**路徑**|
|---|---|
|MessageSender|`PIXIS.ProbePortWorker/Service/MessageSender.cs`|
|ProbeDaemonConnection|`PIXIS.ProbePortWorker/SignalR/ProbeDaemonConnection.cs`|
|DaemonSocketProxyServer|`PIXIS.ProbePortWorker/BackgroundWorker/DaemonSocketProxyServer.cs`|
|PortWorkerHub|`PIXIS.ProbeDaemonWorker/SignalR/PortWorkerHub.cs`|
|CoreServiceConnection|`PIXIS.ProbeDaemonWorker/SignalR/CoreServiceConnection.cs`|
|ProbeDaemonHub|`PIXIS.CoreServiceWorker/SignalR/ProbeDaemonHub.cs`|
|PortWorkerRequestService|`PIXIS.Core.Service/PortWorkerRequestService.cs`|
