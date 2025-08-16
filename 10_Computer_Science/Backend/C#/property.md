針對存取和修改private field，C#提供syntax sugar（Property）能快速設定

**命名慣例：**

- 屬性的名稱應該使用帕斯卡命名法（Pascal Case），即每個單字的開頭都大寫。例如：`MyProperty`。

傳統寫法：
``` C#
public class MyClass
{
    private int myPrivateField;

    public int GetMyField()
    {
        return myPrivateField;
    }

    public void SetMyField(int value)
    {
        myPrivateField = value;
    }
}

class Program
{
    static void Main()
    {
        MyClass myInstance = new MyClass();
        myInstance.SetMyField(42);
        int value = myInstance.GetMyField();
        Console.WriteLine($"MyField Value: {value}");  // 輸出: MyField Value: 42
    }
}

```

Property寫法：
```C#
public class MyClass
{
    private int myPrivateField;

    public int MyProperty
    {
        get
        {
            return myPrivateField;
        }
        set
        {
            myPrivateField = value;
        }
    }
}

class Program
{
    static void Main()
    {
        MyClass myInstance = new MyClass();
        myInstance.MyProperty = 42;
        int value = myInstance.MyProperty;
        Console.WriteLine($"MyProperty Value: {value}");  // 輸出: MyProperty Value: 42
    }
}

```
`value` 是 `set` 存取器中用於表示將要賦予給field的新值