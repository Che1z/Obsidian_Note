# DLL (Dynamic Link Library)

DLL (動態連結程式庫) 是 C# 原始碼 (`.cs`) 經過編譯後產生的檔案類型之一，在 .NET 生態系中，它通常被稱為「程式集 (Assembly)」，是程式碼重用和模組化的核心。

`.cs` (C# 原始碼) --(編譯)--> `.dll` (程式集)

---

## 核心概念

- **程式集 (Assembly)**: 在 .NET 中，DLL 是一種程式集。它是部署、版本控制和安全權限的最小單位。
- **可重用性**: DLL 允許多個不同的應用程式共用同一份程式碼，避免重複開發。
- **模組化**: 將應用程式的不同功能拆分成獨立的 DLL，可以讓專案結構更清晰，更易於維護和更新。

---

## DLL vs. EXE

| 特性 | DLL (類別庫) | EXE (可執行檔) |
| :--- | :--- | :--- |
| **啟動方式** | 無法獨立執行，需由其他應用程式呼叫 | 可以獨立執行 |
| **進入點** | 沒有 `Main` 方法 | 包含 `Main` 方法作為程式進入點 |
| **用途** | 封裝可共用的類別、函式庫 | 作為應用程式的主體 |

---

## 如何建立與使用 DLL

### 建立 DLL
在 Visual Studio 中，可以透過建立「**類別庫 (Class Library)**」專案來產生 DLL 檔案。

### 使用 DLL
在需要使用該 DLL 的專案中，可以透過「**加入參考 (Add Reference)**」的方式，將其引入。

```csharp
// 假設已參考 MyLibrary.dll
using MyLibrary;

public class Program
{
    public static void Main()
    {
        // 使用 MyLibrary.dll 中定義的類別
        MyClass myObject = new MyClass();
        myObject.SomeMethod();
    }
}
```

---

## 優點
- **程式碼重用**: 減少重複撰寫相同的邏輯。
- **易於維護**: 更新 DLL 後，所有參考它的應用程式都能獲取更新，無需重新編譯主程式。
- **關注點分離**: 將不同功能的程式碼分離到不同的 DLL 中，降低耦合度。
