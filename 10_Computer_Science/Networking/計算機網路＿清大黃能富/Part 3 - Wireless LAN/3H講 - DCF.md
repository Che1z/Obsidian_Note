
2024/10/29

Ｑ：如何讓端點分享頻寬避免碰撞？

	在 DCF 中，CSMA/CA 負責監聽頻道並避免碰撞，隨機退避時間則讓各個工作站在頻道空閒時有不同的傳輸時間，進而降低碰撞發生的概率

![[Pasted image 20241029100103.png]]
Carrier sense有兩種：實體和虛擬
PHY : physical layer
NAV : 透過RTS/CTS Frame中告知的持續時間來預測未來流量



![[Pasted image 20241029100135.png]]傳送與接收端在實際傳送Data frame前，先透過交換 RTS 和 CTS Frame (包含了持續時間)， 來告知其他工作站傳輸媒介已被預約(忙碌)的資訊

此機制只能使用在單播 (unicast)，不能使用在群播(multicast)或廣播(broadcast)

RTS_Threshold : Frame資料長度低於此門檻就不需使用 RTS/CTS機制, 可直接傳送

![[Pasted image 20241029101204.png]]
媒體存取控制層：MAC-Level

![[Pasted image 20241029101727.png]]
### 具體等待時間差異

通常，這些等待時間是根據標準的時間單位設定的，例如：

- **SIFS (Short Inter Frame Space)**：最短，通常用於 ACK 和 CTS 等控制幀的回應。
- **PIFS**：稍長於 SIFS，但短於 DIFS，供 AP 使用，以優先於 DCF 節點。
- **DIFS**：最長，通常用於一般節點在競爭期 CP 中發送數據。

這樣的 IFS 設計確保了不同模式和不同優先級流量之間的協調與公平性。
![[Pasted image 20241029103051.png]]

即使 **Station** 或 **AP** 等了 **PIFS** 或 **DIFS** 的時間長度後，也不代表可以立刻傳送封包，還需要再經過 **Random Backoff Time** 以避免碰撞的情況發生

原因：減少多個節點同時嘗試傳輸而導致的 **碰撞**

如何計算？

- **Slot Time** 是一個固定的時間單位，用來避免碰撞的延遲時間
- **Backoff Time** 是一個隨機選取的 Slot Time 倍數，用於確保每個節點的傳輸時機不同，以降低碰撞機率。


![[Pasted image 20241029103455.png]]

Slot time : transmitter開啟時間 ＋ 信號在空氣中傳輸的延遲 ＋ 檢測媒介是否空閒的延遲

```C
### 例子說明

假設在 IEEE 802.11b 中，定義的 CW 值範圍如下：

- CWmin = 15（即 0 到 15）
- CWmax = 1023（即 0 到 1023）

#### 假設以下流程：

1. 第一次碰撞
    
    - CW 值從 CWmin 開始，範圍為 0 到 15。
    - 節點從 0 到 15 中隨機選取一個整數作為 Backoff Time 的倍數，例如選到 `7`。
    - Backoff Time = 7 × Slot Time。
2. 第二次碰撞
    
    - 發生碰撞後，CW 值加倍，即：CW = 2 × (15 + 1) - 1 = 31。
    - 此時，範圍變成 0 到 31。
    - 節點從 0 到 31 中選擇一個隨機整數，例如選到 `12`。
    - Backoff Time = 12 × Slot Time。
3. 第三次碰撞
    
    - 再次碰撞後，CW 繼續加倍：CW = 2 × (31 + 1) - 1 = 63。
    - 範圍擴大為 0 到 63。
    - 節點從 0 到 63 中選擇一個隨機整數，例如選到 `25`。
    - Backoff Time = 25 × Slot Time。
4. CW 到達上限
    
    - 如果繼續發生碰撞，CW 值會繼續倍增，直到達到 CWmax（1023）。
    - 一旦達到 CWmax，就不再增加，保持在最大值 1023。
```
