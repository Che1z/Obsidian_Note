**用法：**

區分 Class 中的不同 Constructor（過載）：
當一個類別中有多個建構子（Constructor）時，可以使用 `this` 來區分不同的建構子。這樣可以在一個建構子中呼叫同一類別的其他建構子，以重用共通的初始化邏輯。
``` C#
public class MyClass
{
    private int myField;

    // 第一個Constructor
    public MyClass()
        : this(0) // 調用另一個Constructor
    {
    }

    // 第二個Constructor，接受參數
    public MyClass(int initialValue)
    {
        myField = initialValue;
    }
}
```


在 Class 的方法內部，`this` 代表當前實例（Current Instance），用於區分類別成員和局部變數（參數）:
``` C#
public class MyClass
{
	// 類別成員
    private int myField;

    // 建構子
    public MyClass(int myField)
    {
		// this.myField 是類別(Class)成員，myField 是建構子的參數（區域變數）
        this.myField = myField;
    }

    // 方法
    public void PrintFieldValue()
    {
        // 使用 this 引用類別成員
        Console.WriteLine($"Class field value: {this.myField}");
    }
}

```