# Eager Singleton 模式

## 概述

Eager Singleton（急切單例）是設計模式中單例模式的一種實現方式。與 Lazy Singleton（懶惰單例）不同，Eager Singleton 在類別加載時就立即創建實例，而不是等到第一次被請求時才創建。

## 實現特點

1. **立即初始化**：在類別載入時就建立實例
2. **私有建構子**：防止外部直接實例化
3. **靜態唯一實例**：使用靜態欄位保存唯一實例
4. **公開訪問方法**：提供公開方法獲取唯一實例

## 程式碼範例

```csharp
public class EagerSingleton
{
    // 1️⃣ 在類別載入時就直接建立實例（eager）
    private static readonly EagerSingleton _instance = new EagerSingleton();

    // 2️⃣ 建構子設為 private，外部不能 new
    private EagerSingleton()
    {
        Console.WriteLine("EagerSingleton 被建立");
    }

    // 3️⃣ 提供公開方法取用唯一實例
    public static EagerSingleton Instance => _instance;

    public void DoSomething()
    {
        Console.WriteLine("做一些事");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // 第一次使用 Instance，才觸發 static 欄位初始化
        var s1 = EagerSingleton.Instance;
        s1.DoSomething();

        var s2 = EagerSingleton.Instance;
        s2.DoSomething();

        // 比對是否同一個實例
        Console.WriteLine(object.ReferenceEquals(s1, s2));  // ✅ True
    }
}
```

## 程式碼解析

### 1. 靜態唯一實例

```csharp
private static readonly EagerSingleton _instance = new EagerSingleton();
```

- 這行程式碼在類別載入時就被執行，立即創建 EagerSingleton 的實例
- 使用 `readonly` 確保實例不會被修改
- 使用 `static` 確保在整個應用程式中只有一個實例

### 2. 私有建構子

```csharp
private EagerSingleton()
{
    Console.WriteLine("EagerSingleton 被建立");
}
```

- 將建構子設為 `private`，防止外部程式碼直接使用 `new` 關鍵字創建實例
- 確保實例只能通過靜態 `Instance` 屬性獲取

### 3. 公開訪問方法

```csharp
public static EagerSingleton Instance => _instance;
```

- 提供公開的靜態屬性，允許外部程式碼訪問唯一實例
- 使用 C# 的表達式體成員語法（`=>` 運算符）簡潔地實現

## Eager Singleton 的優點

1. **線程安全**：由於實例在類別載入時就創建，避免了多線程環境下的競態條件問題
2. **實現簡單**：不需要額外的同步機制或雙重檢查鎖定
3. **確定性初始化**：實例總是在程式啟動時創建，行為更可預測

## Eager Singleton 的缺點

1. **無論是否使用都會創建**：即使應用程式從未使用該單例，也會創建實例並佔用資源
2. **無法處理例外**：如果實例化過程拋出例外，無法在使用時進行處理
3. **無法使用參數**：不支持基於運行時參數創建實例

## 適用場景

Eager Singleton 適合以下場景：

- 實例的創建不耗費太多資源
- 應用程式總是會使用該實例
- 需要在啟動時確保單例存在
- 多線程環境下需要確保線程安全且不希望引入顯式同步
