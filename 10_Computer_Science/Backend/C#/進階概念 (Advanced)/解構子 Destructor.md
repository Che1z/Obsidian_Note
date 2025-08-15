# C# 解構子 (Destructor)

解構子（Destructor，也稱為finalizers）是一種特殊方法，用於在物件被垃圾回收前釋放非受控資源。
在 C#中，解構子的語法使用類別名稱前加上波浪符號 (~)。

## 解構子的基本概念

解構子有以下主要特性：

- 名稱與類別相同，並在前面加上波浪符號 (~)
- 不接受參數且不能被重載
- 無法直接呼叫，由垃圾回收器 (GC) 自動調用
- 執行時間不確定，取決於垃圾回收器何時運行
- 無法被繼承或覆寫

## 解構子基本語法

```csharp
// 解構子宣告
public class MyClass
{
    // 建構子
    public MyClass()
    {
        Console.WriteLine("物件建立");
    }

    // 解構子
    ~MyClass()
    {
        Console.WriteLine("物件銷毀");
    }
}

// 使用類別
MyClass obj = new MyClass(); // 輸出: 物件建立
// 當程式結束或obj不再被參考時，解構子會被呼叫
```

## 解構子與 Finalize 方法

解構子在底層被編譯器轉換為 `Finalize` 方法的覆寫。以下兩種寫法等效：

```csharp
~MyClass()
{
    // 清理資源的程式碼
}

// 等同於
protected override void Finalize()
{
    try
    {
        // 清理資源的程式碼
    }
    finally
    {
        base.Finalize();
    }
}
```

## 解構子與 IDisposable 模式 

由於解構子執行時間的不確定性(GC是有資源需求才會執行)，更好的做法是實作 `IDisposable` 介面來<mark style="background: #FFB86CA6;">主動</mark>釋放資源：

```C#
public class ResourceHolder : IDisposable
{
    private bool disposed = false;
    private IntPtr handle; // 非受控資源

    public ResourceHolder()
    {
        // 獲取資源
        handle = GetResource();
    }

    // 實作 IDisposable
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this); // 防止解構子被呼叫
    }

    protected virtual void Dispose(bool disposing)
    {
        if (!disposed)
        {
            if (disposing)
            {
                // 釋放受控資源
            }

            // 釋放非受控資源
            CloseHandle(handle);
            handle = IntPtr.Zero;

            disposed = true;
        }
    }

    ~ResourceHolder()
    {
        Dispose(false);
    }
}

// 使用 using 語句確保資源正確釋放
using (var resource = new ResourceHolder())
{
    // 使用資源
} // 離開範圍後自動呼叫 Dispose
```

## 最佳實踐

1. **盡量避免使用解構子**，優先使用 `IDisposable` 和 `using` 語句
2. 解構子只用於確保[[非受控資源]]在物件被垃圾回收時得到釋放
3. 使用 `GC.SuppressFinalize` 避免已清理資源的物件進入終結器隊列
4. 實作 Dispose Pattern 來管理資源生命週期

## 適用場景

解構子主要用於釋放以下類型的非受控資源：

- 檔案操作句柄
- 資料庫連接
- COM 物件
- 網路連接
- 非受控記憶體

## 解構子的執行順序

在物件繼承鏈中，解構子的執行順序與建構子相反：

- 建構子：從基底類別到派生類別
- 解構子：從派生類別到基底類別

```csharp
public class Base
{
    public Base() { Console.WriteLine("Base 建構"); }
    ~Base() { Console.WriteLine("Base 解構"); }
}

public class Derived : Base
{
    public Derived() { Console.WriteLine("Derived 建構"); }
    ~Derived() { Console.WriteLine("Derived 解構"); }
}

// 執行結果
// Base 建構
// Derived 建構
// ...
// Derived 解構
// Base 解構
```
