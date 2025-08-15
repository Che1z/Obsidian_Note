Inter Frame Space：封包與封包間的時間間隔


在 IEEE 802.11 無線網路中，**PCF** 的 **PIFS (PCF Inter Frame Space)** 比 **DCF** 的 **DIFS (DCF Inter Frame Space)** 短，是為了讓 **PCF** 擁有更高的優先權。

因為 **PIFS** 的等待時間比 **DIFS** 短，所以當網路同時支持 **PCF** 和 **DCF** 時，AP 可以在 **PIFS** 間隔後搶先獲得通道控制權，從而開始 **PCF** 的輪詢機制，允許它優先於 **DCF** 的節點發送數據。
這樣一來，**PCF** 就可以在無需競爭的情況下為關鍵應用（例如語音或視頻傳輸）提供更高的服務保證。
