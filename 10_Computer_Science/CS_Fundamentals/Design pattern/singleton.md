Singleton Pattern (單例模式)

## 說明

Singleton 模式是一種創建型設計模式，它確保一個類別只有一個實例，並提供一個全域的訪問點來獲取這個實例。

## 使用時機

- 當你需要確保一個類別在整個應用程式中只有一個實例時。
- 當你需要一個全域的訪問點來訪問這個實例時。

## 優點

- **確保唯一實例：** 這是 Singleton 模式最主要的優點，可以避免因為創建多個實例而導致的狀態不一致或資源浪費。
- **全域訪問點：** 提供一個方便的方式來訪問唯一的實例，而不需要在程式碼中到處傳遞這個實例。
- **延遲初始化 (Lazy Initialization)：** 可以在第一次需要時才創建實例，避免在應用程式啟動時就創建不必要的物件。

## 缺點

- **違反單一職責原則 (Single Responsibility Principle)：** Singleton 類別除了負責自己的業務邏輯外，還需要負責管理自己的實例。
- **可能隱藏依賴關係：** 當一個類別直接在內部使用 Singleton 時，會隱藏這個類別對 Singleton 的依賴關係，使得測試和維護變得困難。
- **多執行緒環境下的問題：** 在多執行緒環境下，需要特別處理以確保執行緒安全，避免創建多個實例。

## C# 實作

```csharp
public sealed class Singleton
{
    // 私有的靜態變數，用來儲存唯一的實例
    private static Singleton _instance = null;

    // 私有的建構函式，防止外部直接實例化
    private Singleton() { }

    // 公開的靜態方法，用來獲取唯一的實例
    public static Singleton Instance
    {
        get
        {
            // 如果實例不存在，則創建一個新的實例
            if (_instance == null)
            {
                _instance = new Singleton();
            }
            return _instance;
        }
    }

    // 其他的商業邏輯
    public void DoSomething()
    {
        Console.WriteLine("Singleton is doing something.");
    }
}
```

## 使用 `Lazy<T>` 實現 Singleton

使用 `Lazy<T>` 可以更簡單、更安全地實現 Singleton 模式，特別是在多執行緒環境下。`Lazy<T>` 會自動處理執行緒安全問題，並確保只有在第一次訪問時才會創建實例。

```csharp
public sealed class SingletonWithLazy
{
    // 使用 Lazy<T> 來延遲初始化 Singleton 實例
    private static readonly Lazy<SingletonWithLazy> _lazy =
        new Lazy<SingletonWithLazy>(() => new SingletonWithLazy());

    // 私有的建構函式，防止外部直接實例化
    private SingletonWithLazy() { }

    // 公開的靜態屬性，用來獲取唯一的實例
    public static SingletonWithLazy Instance
    {
        get
        {
            return _lazy.Value;
        }
    }

    // 其他的商業邏輯
    public void DoSomething()
    {
        Console.WriteLine("SingletonWithLazy is doing something.");
    }
}
```

## 總結

Singleton 模式是一個簡單而強大的設計模式，但在使用時也需要注意其潛在的缺點。在 C# 中，建議使用 `Lazy<T>` 來實現 Singleton 模式，以確保執行緒安全和延遲初始化。
''