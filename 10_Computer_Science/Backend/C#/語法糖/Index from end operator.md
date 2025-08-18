# C# 從結尾索引 (Index from End Operator)

從 C# 8.0 開始，您可以使用 `^` 運算子來存取序列（如陣列或列表）中從結尾算起的元素。

```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
int lastElement = numbers[^1];  // 得到最後一個元素，即 5
int secondToLast = numbers[^2]; // 得到倒數第二個元素，即 4
```

---

### 為何這是語法糖？

`^` 運算子是一種語法糖，它讓「從後面存取元素」這個常見操作變得非常直觀。編譯器會將 `numbers[^n]` 這樣的語法轉換成 `numbers[numbers.Length - n]`。這避免了手動計算索引的麻煩，也讓程式碼更具可讀性。

---

### 不使用語法糖的寫法

在 C# 8.0 之前，若要從結尾存取元素，您需要手動用集合的總長度來減去您想要的索引位置。

```csharp
int[] numbers = { 1, 2, 3, 4, 5 };

// 取得最後一個元素
int lastElement = numbers[numbers.Length - 1]; // 得到 5

// 取得倒數第二個元素
int secondToLast = numbers[numbers.Length - 2]; // 得到 4
```
