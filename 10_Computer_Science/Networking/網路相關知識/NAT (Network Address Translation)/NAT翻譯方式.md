

💡 **NAT 可分為四種方式翻譯 IP Address**

- Static NAT
- Static PAT
- Dynamic NAT
- Dynamic PAT

🔹 **NAT vs PAT**

- NAT：經過 Router (L3設備) 後，只變動 L3 header
- PAT：經過 Router 後，變動 L3 和 L4 header

> 註：NAT 屬於 L3 技術，封包結構為 4 header + L3 header + data


🔹**Static vs Dynamic**

- Static：翻譯前後的 IP 明確定義，Router 無需決策
    - 例：看到 192.168.0.1 就轉成 72.9.4.22
        
- Dynamic：管理者定義規則，Router 介入決定最終公共 IP
    - 例：看到 192.168.0.0/24 轉成 72.9.4.22、72.9.4.23、72.9.4.24

🔹 **四種 NAT/PAT 概念整理**

- **Static NAT**：固定 1 對 1 IP 轉換，Port 不變
- **Dynamic NAT**：動態 1 對多 IP 轉換，Port 不變
- **Static PAT**：固定 1 對 1 IP + Port 轉換
- **Dynamic PAT**：多對 1 IP + Port 轉換，多個內部 host 共用公共 IP



| 類型                               | IP 轉換             | Port 轉換 | 特點                 | 適用情境                  |
| -------------------------------- | ----------------- | ------- | ------------------ | --------------------- |
| **Static NAT**                   | 固定 1 對 1          | 無       | 映射固定，Router 無需決策   | 內部伺服器對外提供固定 IP 服務     |
| **Dynamic NAT**                  | 動態 1 對多（從 IP 池分配） | 無       | Router 根據可用 IP 池決定 | 內部使用者臨時對外訪問           |
| **Static PAT** (Port Forwarding) | 固定 1 對 1          | 修改      | 對外服務特定 port        | 外部訪問特定內部服務            |
| **Dynamic PAT** (NAT Overload)   | 多對 1              | 修改      | 多個內部使用者共用單一公共 IP   | 家庭或企業內部多台設備共用公共 IP 上網 |
