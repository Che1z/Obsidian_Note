2024/10/28

![[Pasted image 20241028161912.png]]

### 1. MAC Header

- 整個 MAC Header 大小為 24-30 bytes，包含控制、地址等訊息，負責網絡資料傳輸的控制。

### 2. Frame Control (2 bytes)

- **Protocol Version (2 bits)**：表示協議版本，通常是 `00`。
- **Type (2 bits)**：框架的類型，IEEE 802.11 中有三種類型：Management、Control 和 Data。
- **Subtype (4 bits)**：框架的子類型，例如 Beacon、ACK、Data 等。
- **To DS (1 bit)**：指示數據是否發往 Distribution System（DS）。
- **From DS (1 bit)**：指示數據是否來自 DS。
- **More Fragments (1 bit)**：指示是否有更多片段。
- **Retry (1 bit)**：標記此框架是否是重發的。
- **Power Management (1 bit)**：指示設備的省電模式。
- **More Data (1 bit)**：指示是否有更多數據需要傳輸。
- **Protected Frame (1 bit)**：表示此框架是否受加密保護。
- **Order (1 bit)**：設置是否使用嚴格排序交付。

### 3. Duration / Connection ID (2 bytes)

- 指示資料框架的預期持續時間，或者在某些控制框架中作為識別碼。

### 4. Address Fields

- **Address 1 (6 bytes)**：目標地址（接收設備的 MAC 地址）。
- **Address 2 (6 bytes)**：來源地址（發送設備的 MAC 地址）。
- **Address 3 (6 bytes)**：通常為 AP 地址，或是中繼 AP 的 MAC 地址。
- **Address 4 (6 bytes)**：當使用無線分佈系統（WDS）時才會用到，表示中繼的目標地址。

### 5. Sequence Control (2 bytes)

- 包括 **Fragment Number (4 bits)** 和 **Sequence Number (12 bits)**，用於重組片段及確認資料包的順序。

### 6. Data (0-2312 bytes)

- 實際的數據內容，大小範圍為 0 到 2312 bytes，依據 MTU 和傳輸協議而定。

### 7. Frame Check Sequence (FCS) (4 bytes)

- 用於錯誤檢測的校驗碼，採用 CRC-32 算法來確保數據的完整性。