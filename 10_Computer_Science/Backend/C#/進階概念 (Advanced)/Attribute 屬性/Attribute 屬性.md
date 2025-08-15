# C# Attribute（屬性）

Attribute（屬性）是 C# 中用於為程式碼元素添加[[元數據 Metadata]] 的宣告性標記。屬性可以應用於程式集、模組、類型、成員和參數等。

## Attribute 的基本概念

Attribute 以中括號 `[AttributeName]` 的形式標記在程式碼元素上方，為程式碼提供額外信息。

```csharp
[AttributeName]
public class MyClass
{
}
```

## Attribute 的特點

- 所有屬性都繼承自 `System.Attribute` 基類
- 可以透過反射（Reflection）在運行時讀取
- 不直接影響程式碼行為，但可以被用來改變行為
- 可以攜帶參數和數據

## 定義自訂 Attribute

```csharp
// 自訂屬性定義
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method, AllowMultiple = true)]
public class DeveloperInfoAttribute : Attribute
{
    public string DeveloperName { get; }
    public string LastModified { get; }

    public DeveloperInfoAttribute(string developerName, string lastModified)
    {
        DeveloperName = developerName;
        LastModified = lastModified;
    }
}

// 使用自訂屬性
[DeveloperInfo("張三", "2023-04-15")]
public class PaymentProcessor
{
    [DeveloperInfo("李四", "2023-05-20")]
    public void ProcessPayment()
    {
        // 實作
    }
}
```

## 常見的內建 Attribute

```csharp
// 標記已淘汰的方法，提供警告
[Obsolete("此方法即將棄用，請改用NewMethod()")]
public void OldMethod() { }

// 指定可序列化類型
[Serializable]
public class User { }

// 排除不需要序列化的欄位
public class Customer
{
    public int Id { get; set; }
    [NonSerialized]
    private string _tempPassword;
}

// 編譯器指令
[MethodImpl(MethodImplOptions.AggressiveInlining)]
public static int Add(int a, int b) => a + b;

// 條件編譯
[Conditional("DEBUG")]
public void DebugLog(string message)
{
    Console.WriteLine(message);
}
```

## 使用反射讀取 Attribute

```csharp
public static void DisplayTypeAttributes(Type type)
{
    var attributes = type.GetCustomAttributes(false);
    foreach (var attr in attributes)
    {
        if (attr is DeveloperInfoAttribute devAttr)
        {
            Console.WriteLine($"開發者: {devAttr.DeveloperName}");
            Console.WriteLine($"最後修改: {devAttr.LastModified}");
        }
    }
}
```

## Attribute 的常見用途

- 配置和元數據（如 Web API 路由）
- 編譯器指令（如 Obsolete）
- 運行時行為控制（如 Serializable）
- 程式碼分析和工具支持
- 相依性注入標記
- 文檔生成
