**ARP（Address Resolution Protocol）** 是網路傳輸中非常重要的概念。
以下是概述、作用以及運作方式的說明：

### ARP（Address Resolution Protocol）

ARP 是一種網路協定，用於解析 IP 位址到 MAC 位址的對應關係。
由於 IP 封包在以太網（Ethernet）上傳輸時，實際是依靠 MAC 位址來決定網路上資料傳輸的最終目標，ARP 協定就用來查詢 IP 位址對應的 MAC 位址，特別是當主機間通信發生在同一個網段時。

#### ARP 的作用

在同一網段內的兩台設備通信時，IP 位址是屬於邏輯位址，而以太網則需要依賴物理位址（MAC 位址）來實際傳送資料。
ARP 協定可以根據已知的 IP 位址查詢其對應的 MAC 位址，確保資料能夠被正確傳送到目標設備。

#### ARP 的運作機制

1. **ARP 請求**（Request）：當主機 A 想要和主機 B 通信時，若主機 A <mark style="background: #FFF3A3A6;">知道主機 B 的 IP 位址但不知道其 MAC 位址</mark>，A 會發送一個 ARP 請求廣播訊息。
   ARP 請求包含了 B 的 IP 位址，並且要求與該 IP 位址對應的設備回覆其 MAC 位址。
    
2. **ARP 回應**（Reply）：當網段內的其他設備接收到 ARP 廣播訊息時，它們會檢查自己的 IP 位址。
   如果某台設備發現 ARP 請求中的 IP 位址和自身匹配，它會回應一個 ARP 回應，並提供其 MAC 位址。
   主機 A 接收到該 ARP 回應後，就可以將 IP 位址和 MAC 位址對應起來。
    
3. **ARP 快取**：為了避免頻繁查詢，ARP 協定會將 IP 與 MAC 對應關係暫存於 ARP 快取（Cache）中，一段時間內重複利用該對應資訊，節省網路資源。
    

### 範例說明

假設電腦 A 需要向電腦 B 發送封包，但只有 B 的 IP 位址而無法直接取得 MAC 位址。A 會先透過 ARP 發送請求來查詢 B 的 MAC 位址。取得 MAC 位址後，A 就能組裝包含 B 的 MAC 位址的 Ethernet Frame 並發送封包。隨後，這些封包會依據目標的 MAC 位址正確抵達 B。

### 總結
- **ARP 協定** 用於解析 IP 到 MAC 位址，確保在同一網段中的設備能夠根據 IP 位址找到對應的 MAC 位址來傳送資料。
- ARP可算是Layer2和Layer3之間的橋樑