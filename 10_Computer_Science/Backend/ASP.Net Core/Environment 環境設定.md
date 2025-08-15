# ASP.NET Core 環境設定

## 環境變數機制

ASP.NET Core 使用 `ASPNETCORE_ENVIRONMENT` 環境變數來決定應用程式的執行環境。這是一個彈性的設計，允許開發者自定義環境名稱。

## 常見環境名稱

雖然不是硬性規定的預設值，但以下三個環境名稱是最常見且被廣泛使用的：

1. **Development**

   - 用途：本地開發和測試
   - 特點：
     - 啟用詳細錯誤頁面
     - 使用開發用設定
     - 適合使用測試/偽資料

2. **Staging**

   - 用途：部署前的測試環境
   - 特點：
     - 模擬生產環境
     - 使用真實資料流
     - 測試部署流程

3. **Production**
   - 用途：實際運行環境
   - 特點：
     - 啟用所有安全設定
     - 啟用效能最佳化
     - 簡化錯誤頁面

## 環境設定方式

### 1. 開發階段（launchSettings.json）

```json
{
  "profiles": {
    "YourProject": {
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

### 2. 系統環境變數

- Windows CMD：

```cmd
set ASPNETCORE_ENVIRONMENT=Production
```

- Linux/macOS：

```bash
export ASPNETCORE_ENVIRONMENT=Staging
```

## 重要說明

1. **非硬性限制**

   - 這三個環境名稱不是 ASP.NET Core 硬編碼的唯一選項
   - 開發者可以自定義其他環境名稱（如 QA、Test、UAT 等）

2. **內建功能支援**

   - 許多 ASP.NET Core 內建功能（如 `appsettings.{Environment}.json`）預期使用這些環境名稱
   - 錯誤處理中介軟體等也會根據這些環境名稱調整行為

3. **為什麼需要不同環境**

   - 安全性考量：不同環境需要不同的安全設定
   - 錯誤處理：開發環境需要詳細錯誤訊息，生產環境則需要簡化
   - 資料來源：開發環境可能使用測試資料，生產環境使用真實資料
   - 維護性：分離環境設定使維護更容易

4. **彈性設計的優點**
   - 允許團隊根據需求自定義環境
   - 支援不同開發流程和部署策略
   - 可以根據專案需求添加其他環境（如 UAT、Test 等）

