# C# 屬性 (Property)

屬性（Property）是 C# 提供的一種語法糖，讓您可以像存取公開欄位（Public Field）一樣，簡單地存取與修改私有欄位（Private Field），同時保有方法的封裝性。

---

### 為何這是語法糖？

屬性看起來像是公開的類別成員，但它們實際上是特殊的方法，分別稱為 `get` 存取子和 `set` 存取子。當您編譯程式碼時，編譯器會將屬性轉換成底層的 `get_PropertyName()` 和 `set_PropertyName(value)` 方法。

這種寫法讓您可以用更簡潔、直觀的方式來控制欄位的存取，而不需要明確地呼叫 getter 和 setter 方法。

---

### 不使用語法糖的寫法 (傳統 Getter/Setter)

在沒有屬性語法糖之前，開發者需要手動建立 `Get` 和 `Set` 方法來封裝一個私有欄位。

```C#
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

---

### 使用屬性的寫法

屬性語法將上述的 Getter/Setter 方法簡化成一個程式碼區塊。

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
            // `value` 是 set 存取器中的隱含參數，代表要賦予的新值
            myPrivateField = value;
        }
    }
}

class Program
{
    static void Main()
    {
        MyClass myInstance = new MyClass();
        myInstance.MyProperty = 42; // 內部呼叫 set 存取子
        int value = myInstance.MyProperty; // 內部呼叫 get 存取子
        Console.WriteLine($"MyProperty Value: {value}");  // 輸出: MyProperty Value: 42
    }
}
```
**命名慣例：** 屬性的名稱應該使用帕斯卡命名法（Pascal Case），即每個單字的開頭都大寫。例如：`MyProperty`。
