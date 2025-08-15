# DLL (Dynamic Link Library)

dll 是 c#檔案編譯過後檔案類型
.cs --> .dll (透過 compilation)

## 基本概念

- **DLL 定義**：動態連結程式庫（Dynamic Link Library），是 Windows 系統中可供多個程式共用的程式碼和資源集合。
- **執行方式**：DLL 不能獨立執行，必須由應用程式或其他 DLL 呼叫。
- **副檔名**：通常為 `.dll`，但 .NET 程式集也可以是 `.exe`（可執行檔）。

## DLL 與 EXE 的區別

| DLL                  | EXE                        |
| -------------------- | -------------------------- |
| 不可獨立執行         | 可獨立執行                 |
| 需被其他程式呼叫     | 有自己的進入點 (Main 方法) |
| 可被多個應用程式共用 | 通常是單一應用程式         |
| 一般無使用者介面     | 可以有使用者介面           |

## .NET 中的 DLL

在 .NET 中，DLL 通常指的是程式集 (Assembly)，它是 .NET 應用程式的部署和版本管理的基本單位。

### 程式集組成

- **IL 程式碼**：編譯後的中間語言 (Intermediate Language) 程式碼
- **中繼資料**：型別定義、參考的組件等
- **清單** (Manifest)：程式集身份、版本、文化特性等

## 建立 DLL

### 使用 Visual Studio

1. 建立新專案，選擇「類別庫」(Class Library) 專案範本
2. 撰寫程式碼
3. 建置專案，輸出 DLL 檔案

### 使用命令列

```bash
dotnet new classlib -n MyLibrary
cd MyLibrary
# 編輯程式碼
dotnet build
```

## 使用 DLL

### 在專案中加入參考

1. **Visual Studio**：在「參考」上按右鍵，選擇「加入參考」
2. **專案檔方式**：
   ```xml
   <ItemGroup>
     <Reference Include="MyLibrary">
       <HintPath>path\to\MyLibrary.dll</HintPath>
     </Reference>
   </ItemGroup>
   ```
3. **NuGet 方式**：如果 DLL 已發佈為 NuGet 套件
   ```bash
   dotnet add package MyLibrary
   ```

### 程式碼中使用

```csharp
using MyLibrary;

public class Program
{
    public static void Main()
    {
        // 使用 DLL 中的類型
        MyClass obj = new MyClass();
        obj.MyMethod();
    }
}
```

## DLL 的優點

1. **程式碼重用**：多個應用程式可共用相同的功能
2. **減少記憶體使用**：共用的 DLL 只需載入一次到記憶體
3. **模組化**：將應用程式分解為多個元件
4. **更新便利性**：可以單獨更新 DLL 而不必重新編譯整個應用程式
5. **程式碼分離**：將業務邏輯與基礎設施分離

## 強名稱程式集 (Strong-Named Assembly)

強名稱程式集是帶有數位簽章的程式集，提供唯一身份識別和完整性保證。

### 建立強名稱程式集

1. 使用 `sn.exe` 工具生成強名稱金鑰檔案 (.snk)
   ```bash
   sn -k MyKey.snk
   ```
2. 在專案中使用金鑰檔案
   ```csharp
   [assembly: AssemblyKeyFile("MyKey.snk")]
   ```
   或在專案檔中：
   ```xml
   <PropertyGroup>
     <SignAssembly>true</SignAssembly>
     <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
   </PropertyGroup>
   ```

## 版本控制

DLL 版本控制在大型專案中很重要，可通過以下方式設定：

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]
```

或者在新的 SDK 專案中：

```xml
<PropertyGroup>
  <Version>1.0.0</Version>
  <AssemblyVersion>1.0.0.0</AssemblyVersion>
  <FileVersion>1.0.0.0</FileVersion>
</PropertyGroup>
```

## 常見問題

### DLL 地獄 (DLL Hell)

當多個應用程式依賴同一 DLL 的不同版本時，可能導致衝突和兼容性問題。

### 解決方案

1. **側載 (Side-by-side execution)**：.NET 允許同一 DLL 的多個版本同時存在
2. **強名稱程式集**：提供版本控制和唯一識別
3. **組件綁定重定向**：在應用程式配置檔中指定 DLL 版本重定向

### 全域組件快取 (GAC)

.NET Framework 中用於存儲強名稱程式集的中央存儲庫。

```bash
# 安裝到 GAC
gacutil /i MyAssembly.dll

# 從 GAC 移除
gacutil /u MyAssembly
```

## .NET Core/.NET 5+ 中的變化

在 .NET Core 和 .NET 5+ 中，GAC 已被移除，組件通常與應用程式一起部署。組件解析更加簡化和可預測。

## 實用案例

- 建立共用的業務邏輯層
- 實作外掛系統
- 建立可重用的元件庫
- 分離介面和實作
