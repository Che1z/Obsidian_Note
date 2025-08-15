2024/10/28

在 IEEE 802.11 無線網路中，**DCF（Distributed Coordination Function）** 和 **PCF（Point Coordination Function）** 是兩種媒體訪問控制機制。
主要區別在於如何控制設備之間的通信方式，以避免碰撞並達成高效的頻寬利用。

![[Pasted image 20241028165252.png]]


### 1. DCF（Distributed Coordination Function）

- **工作原理**：DCF 是一種**競爭式**的服務模式，採用 **CSMA/CA（Carrier Sense Multiple Access with Collision Avoidance）** 協議，讓設備在傳送數據前先「聆聽」通道，確認是否有其他設備正在使用通道。
- **主要流程**：
    1. 設備在發送數據前，先進行「載波偵測」，確保通道空閒。
    2. 若通道忙碌，設備會等待一段隨機時間（使用 **exponential backoff** 演算法），然後重新嘗試發送數據。
    3. 若通道空閒，設備就可以直接發送數據。
    4. 若發送成功，接收端會發送 **ACK（Acknowledgment）** 確認數據已接收。
- **特點**：
    - DCF 主要用於 **[[Ad-Hoc]] 模式**，在多個設備之間公平競爭通道。
    - 因為每個設備都獨立競爭通道，因此在網路負載高的情況下，可能會產生碰撞，導致效率降低。

### 2. PCF（Point Coordination Function）

- **工作原理**：PCF 是一種**非競爭式**的服務模式，依賴於 **AP（Access Point）** 的「集中控制」，設備僅在獲得 AP 的許可後才可傳輸數據。PCF 採用「輪詢」方式來控制傳輸。
- **主要流程**：
    1. 在 PCF 模式下，AP 會主動輪詢（poll）各個設備，詢問它們是否有數據要發送。
    2. 當 AP 輪詢到某個設備時，該設備可以傳送數據，而其他設備則保持等待。
    3. 當設備完成數據傳輸後，AP 會輪詢下一個設備，依次進行。
- **特點**：
    - PCF 模式下無須競爭通道，**適合即時性或具時延敏感性的應用**，例如語音或視頻傳輸。
    - 由於 AP 控制傳輸順序，因此在進行通訊時更具可預測性。
    - 不過，PCF 在現代無線網路中較少被實作，因為需要 AP 支援此模式。


![[Pasted image 20241028172137.png]]
### IEEE 802.11 中的 Superframe 結構

在無線網路中，**Superframe** 是指一個週期性重複的時間架構，主要應用在 **PCF (Point Coordination Function)** 模式下。Superframe 包含兩個主要區段：

1. **競爭式區段 (Contention Period, CP)**：在這個階段，所有節點使用 **DCF (Distributed Coordination Function)** 來訪問通道。
2. **非競爭式區段 (Contention-Free Period, CFP)**：在這個階段，AP 會使用 **PCF** 來輪詢各個節點進行通訊，從而確保無競爭的通訊環境。

### PCF 和 DCF 的優先順序

在 Superframe 中，PCF 和 DCF 通過不同的 **[[IFS]]** 時間間隔來實現優先順序：

- **PIFS (PCF Inter Frame Space)**：PCF 使用的 [[IFS]]，比 DIFS 短，確保 AP 在 CFP 中擁有較高的優先權，無需與其他節點競爭。
- **DIFS (DCF Inter Frame Space)**：DCF 使用的 [[IFS]]，較長的等待時間表示它的優先順序低於 PCF。因此，當 Superframe 切換到 CP 階段時，所有節點需要等待 DIFS 間隔，然後競爭通道。