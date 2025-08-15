# ASP.NET Core 8 中的 Configuration 設計

在 ASP.NET Core 8 中，`Configuration` 的設計模式用來管理應用程式的設定。透過 `Key-Value Pair` 的形式儲存和讀取配置，能夠靈活地支援多種配置來源，並根據不同環境切換設定。

---

## 📂 常見的設定來源

1. **`appsettings.json`**  
   - 最常用的靜態設定檔案，用來定義應用程式中的全域設定，例如資料庫連線字串、API 金鑰等。
   - 可以使用 `appsettings.{Environment}.json` 來針對不同環境定義專屬配置，這些檔案會根據執行環境自動載入。

2. **環境變數 (Environment Variables)**  
   - 適合用來儲存與機密相關的設定或特定於執行環境的變數，這些變數可以在運行時覆蓋其他配置。

3. **命令列參數 (Command-line Arguments)**  
   - 可以通過命令列參數傳遞設定，常用於啟動時動態覆蓋其他設定檔中的值。

4. **Secret Manager**  
   - 開發期間可用來安全儲存敏感資料（例如 API 金鑰、密碼）。這些資料不應該存放於 `appsettings.json` 檔案中。

5. **Azure Key Vault**  
   - 在生產環境下，Azure Key Vault 是一種安全的方式來儲存和管理機密資料，並允許應用程式在雲端中安全地存取敏感資訊。

6. **資料庫或外部服務**  
   - 可以動態從資料庫或外部配置服務載入設定，這樣的配置可適合應用程式運行過程中的即時更新需求。

---

## 🧩 配置的加載順序

ASP.NET Core 8 中的配置系統支援多個來源，並按以下順序載入：
1. `appsettings.json`
2. `appsettings.{Environment}.json`
3. 環境變數
4. 命令列參數

**注意**：當相同的 Key 存在於多個來源時，**後載入的來源** 會覆蓋前面的值。

---

## 🔧 使用方式

ASP.NET Core 8 的應用程式使用 `IConfiguration` 介面來讀取配置值。可以在 `Program.cs` 檔案中設定並讀取：

```csharp
var builder = WebApplication.CreateBuilder(args);

// 讀取 appsettings.json 配置
var settingValue = builder.Configuration["MySettingKey"];

var app = builder.Build();
app.Run();
```


### 設定檔變更監聽：

ASP.NET Core 8 支援監聽設定檔變更，可以透過以下方式實現自動重新載入：
``` C#
builder.Configuration.AddJsonFile("appsettings.json", optional: false, reloadOnChange: true);
```

## 補充功能

- **動態載入：** 配置檔案可以設置為自動重新載入，當檔案內容變更時應用程式會自動更新相應的配置值，避免應用程式需要重啟。
    
- **自訂配置來源：** ASP.NET Core 8 允許透過實作 `IConfigurationProvider` 來擴展自定義的設定來源，這樣可以從非預設的資料來源讀取配置。
