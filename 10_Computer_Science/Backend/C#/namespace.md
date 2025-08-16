namespace是用來區分class或method的可作用範圍，建議使用時參考資料夾結構，方便後續管理
比喻：書櫃的書架，用書架來區分分類（科學、經濟...分類）[[using]]

``` C#
// 定義一個命名空間，可以包含多個類別和其他元素
namespace MyNamespace
{
    // 定義一個類別在命名空間中
    public class MyClass
    {
        // 類別的成員和方法
    }

    // 可以在同一個命名空間中定義其他類別、結構等
    public struct MyStruct
    {
        // 結構的成員
    }
}

```

若是沒特別定義namespace的話，就會是儲存在global namespace
```C#
// 沒有特別定義命名空間的類別
public class MyClass
{
    // ...
}

```
