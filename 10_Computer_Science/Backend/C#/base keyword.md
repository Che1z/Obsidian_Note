C#是可以有多層繼承的:
 人(Base class) --> 學生 --> 工程師
 當呼叫學生class時，會先執行人的constructor再執行學生自身的constructor
 此時會遇到一個問題，如果學生class的constructor需要輸入參數時，該怎輸入呢？
 `base keyword`就是解法

> 如同this keyword指向自身物件(學生)，base keyword指向上層物件(人)
> base keyword只能指上一層class而已
 
 Derived class的呼叫順序是由最底層的base class向上呼叫。

在 C# 中，`base` 關鍵字用於在derived class中訪問base class的成員，如方法、屬性和字段。這個關鍵字提供了一種方式，讓你能夠在derived class中使用或覆寫base class的實作。

1.調用base class的constructor（上一層的Constructor）
``` C#
public class BaseClass
{
    public BaseClass(int value)
    {
        // 基礎類別的構造函數
    }
}

public class DerivedClass : BaseClass
{
    public DerivedClass(int value) : base(value)
    {
        // 派生類別的構造函數
    }
}

```

2.**訪問基礎類別的成員**

```C#
	public class BaseClass
{
    public virtual void SomeMethod()
    {
        Console.WriteLine("BaseClass.SomeMethod");
    }
}

public class DerivedClass : BaseClass
{
    public override void SomeMethod()
    {
        base.SomeMethod();  // 調用基礎類別的方法
        Console.WriteLine("DerivedClass.SomeMethod");
    }
}
```
