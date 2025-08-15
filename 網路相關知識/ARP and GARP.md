# ARP (Address Resolution Protocol)

當設備需要連線時，會發送 ARP 請求，透過[[廣播 (Broadcast)]]查詢特定 [[IP 位址]] 對應的 [[MAC 位址]]。

# GARP (Gratuitous ARP)

設備上線時，會發送 GARP 主動宣告自己的 [[IP 位址]] 與 [[MAC 位址]]。

主要目的：
1.  **更新鄰居的 [[ARP 快取表 (ARP Cache)]]**：確保其他設備有最新的對應資訊。
2.  **偵測 [[IP 衝突 (IP Conflict)]]**：避免網路上有重複的 IP 位址。
