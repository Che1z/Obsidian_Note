# C# this 關鍵字

`this` 關鍵字在 C# 中有兩種主要用途：
1.  在類別內部，代表該類別的「目前實例 (Current Instance)」。
2.  用於建構函式鏈 (Constructor Chaining)，讓一個建構函式可以呼叫同一個類別中的另一個建構函式。

---

### 用途 1：代表目前實例

在類別的方法或建構函式內部，`this` 用於區分類別成員（欄位、屬性）和區域變數（如方法參數），當它們名稱相同時。

```C#
public class MyClass
{
    // 類別成員
    private int myField;

    // 建構子
    public MyClass(int myField)
    {
        // this.myField 是類別成員
        // myField 是建構子的參數
        this.myField = myField;
    }
}
```

---

### 用途 2：建構函式鏈 (語法糖)

當一個類別中有多個建構函式（多載）時，可以使用 `: this(...)` 語法從一個建構函式呼叫另一個，以重用共通的初始化邏輯。

```C#
public class MyClass
{
    private int myField;

    // 主要的建構函式，執行實際的初始化
    public MyClass(int initialValue)
    {
        myField = initialValue;
    }

    // 無參數的建構函式，透過 `: this(0)` 呼叫上面的建構函式
    // 並傳入預設值 0
    public MyClass() : this(0)
    {
        // 這裡可以留空，或加上此建構函式專屬的邏輯
    }
}
```

#### 為何這是語法糖？
建構函式鏈是一種語法糖，它讓「重用初始化邏輯」這個需求變得非常簡潔。如果沒有這個語法，您將需要建立一個私有的 `Init()` 方法，並在所有建構函式中手動呼叫它，這會讓程式碼變得較為冗長。

#### 不使用語法糖的寫法
若不使用 `: this()`，可以建立一個共用的私有方法來處理初始化。

```C#
public class MyClass
{
    private int myField;

    // 共用的私有初始化方法
    private void Initialize(int initialValue)
    {
        myField = initialValue;
    }

    // 主要的建構函式
    public MyClass(int initialValue)
    {
        Initialize(initialValue);
    }

    // 無參數的建構函式
    public MyClass()
    {
        Initialize(0); // 手動呼叫初始化方法
    }
}
```
