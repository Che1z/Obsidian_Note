# C# as 運算子

`as` 運算子用於在相容的參考型別之間執行安全的型別轉換。如果轉換成功，它會回傳轉換後的物件；如果轉換失敗，它會回傳 `null` 而不是拋出例外。

```csharp
object myObject = "Hello World";

// 使用 as 運算子嘗試將 object 轉為 string
string myString = myObject as string;

if (myString != null)
{
    Console.WriteLine("轉換成功: " + myString);
}
else
{
    Console.WriteLine("轉換失敗");
}
```

---

### 為何這是語法糖？

`as` 運算子是一種語法糖，它將「檢查型別是否相容，如果相容就轉換」這個常見模式簡化成一個單獨的操作。它避免了撰寫冗長的 `is` 檢查後再進行強制轉換的程式碼，也避免了使用 `try-catch` 區塊來處理可能失敗的轉換，讓程式碼更流暢。

---

### 不使用語法糖的寫法

若不使用 `as` 運算子，您需要先用 `is` 運算子檢查型別，然後再進行強制轉換。

```csharp
object myObject = "Hello World";
string myString = null;

// 1. 先用 'is' 檢查型別
if (myObject is string)
{
    // 2. 如果型別相符，再進行強制轉換
    myString = (string)myObject;
}

if (myString != null)
{
    Console.WriteLine("轉換成功: " + myString);
}
else
{
    Console.WriteLine("轉換失敗");
}
```
**注意：** `as` 運算子只能用於參考型別或可為 Null 的實值型別。對於不可為 Null 的實值型別（如 `int`），直接轉換失敗會拋出 `InvalidCastException`。
