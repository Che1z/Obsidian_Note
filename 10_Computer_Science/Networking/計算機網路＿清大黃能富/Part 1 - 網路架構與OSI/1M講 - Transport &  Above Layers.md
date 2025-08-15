2024/10/24

![[Pasted image 20241024155550.png]]

### Transport Layer：

1. **Process 是什麼？**
    
    - 是的，這裡的「Process」是指**應用程式進程**。
      每個應用程式或服務在系統中都運行作為一個或多個進程。
      傳輸層負責在不同主機的進程之間傳輸資料。
    - 換句話說，傳輸層提供的是端到端（End-to-End）的連接，確保資料從一台設備上的應用程式進程傳輸到另一台設備上的應用程式進程。
2. **Transport Layer 的協議**：
    
    - **TCP (Transmission Control Protocol)**：提供可靠的傳輸服務。它會進行連接的建立、資料的順序控制、重傳丟失的資料包、錯誤檢測等。TCP 適用於需要高可靠性和完整性的應用，如網頁瀏覽、電子郵件、文件傳輸等。
    - **UDP (User Datagram Protocol)**：提供不可靠的傳輸服務。它不保證資料的傳輸順序、不進行錯誤重傳，也不需要連接建立。因此，UDP 適合即時性要求高但對資料可靠性要求較低的應用，如視頻流媒體、VoIP、在線遊戲等。

![[Pasted image 20241024160711.png]]

### Session Layer：

1. **Session Layer 的作用是什麼？**
    - Session Layer 負責建立、管理和終止不同應用之間的會話（Session）。
      它的主要目的是<mark style="background: #FFF3A3A6;">協調複數個Transport Stream</mark>，使應用能夠持續互動。
    - 在具體應用中，Session Layer 可用於處理長時間連接中的會話控制。
    - 例如，在遠程桌面連接、視頻會議等應用中，Session Layer 負責維持會話狀態，並在連線中斷時提供恢復機制。
    - **Namespace 綁定**：Session Layer 使用命名空間來區分不同的會話，確保數據能夠正確地從一個端點傳遞到對應的應用過程。

### Presentation Layer：

1. **主要關注資料的格式**：
    - Presentation Layer 的主要功能是確保**數據格式一致**，以便不同系統之間可以互相理解。
    - 這層可以進行數據的編碼、解碼、壓縮、加密等操作，將資料轉換為應用可以處理的格式。
    - 例如，在兩台主機之間傳輸圖像或文字時，Presentation Layer 可以將數據從一個系統的格式轉換為另一個系統可理解的格式，如將 JPEG 圖像格式進行解碼或將資料進行加密後傳輸。

### Application Layer：

1. **Application Layer 是什麼？**
    - Application Layer 確實是指直接與應用程序交互的層。
    - 這一層包含具體的應用協議，讓用戶可以通過應用程序進行網路上的數據傳輸。
    - 常見的應用協議包括：
        - **HTTP（HyperText Transfer Protocol）**：用於網頁瀏覽。
        - **FTP（File Transfer Protocol）**：用於文件傳輸。
        - **SMTP（Simple Mail Transfer Protocol）**：用於電子郵件傳輸。
        - **DNS（Domain Name System）**：用於將域名轉換為 IP 地址。
    - 這層的作用是提供應用程序所需的功能，從而實現網路上的數據交互，如網頁瀏覽器、電子郵件客戶端、FTP 客戶端等。

### 總結與補充：

- **Transport Layer** 負責主機之間進程的數據傳輸，TCP 提供可靠的傳輸，UDP 則提供不可靠的即時傳輸。
- **Session Layer** 負責維護和管理應用程序之間的會話，特別是在長時間交互或中斷恢復的場景下有用。
- **Presentation Layer** 則關注數據的格式轉換、編碼、加密與解碼，確保資料可以被不同系統理解。
- **Application Layer** 則是指直接與用戶交互的應用層，包含具體的應用協議，支撐如網頁瀏覽、文件傳輸等應用。
  
  
  ![[Pasted image 20241024164508.png]]