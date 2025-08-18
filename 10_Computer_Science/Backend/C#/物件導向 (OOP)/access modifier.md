```csharp
var rectangle1 = new Rectangle();
Console.WriteLine("Width is: " + rectangle1.width); //無法讀取rectangle1.width
Console.WriteLine("Height is: " + rectangle1.height); //無法讀取rectangle1.height


class Rectangle
{
    int width;  
    int height; 
}
```

因為access modifier預設值為private

``` csharp
var rectangle1 = new Rectangle();
Console.WriteLine("Width is: " + rectangle1.width); // Width is: 0
Console.WriteLine("Width is: " + rectangle1.height);  // Height is: 0


class Rectangle
{
    public Int width;  // public需寫在型別宣告前
    public Int height; // public需寫在型別宣告前
}
```

protected

在 C# 中，當你在base class中使用 `protected` 修飾符來定義方法（或其他成員），這表示這個方法將對於derived class是可見的，並且可以在derived class中被調用。

Note：只代表derived class可見，不代表會自動繼承


```C#
public class Animal
{
    // protected 方法
    protected void ProtectedMethod()
    {
        Console.WriteLine("This is a protected method in the base class");
    }
}

public class Dog : Animal
{
    public void AccessProtectedMethod()
    {
        // 在derived class中可以訪問base class的 protected 方法
        ProtectedMethod();
    }
}

class Program
{
    static void Main()
    {
        Dog dog = new Dog();
        dog.AccessProtectedMethod(); // 可以呼叫派生類別中的公開方法，這個方法內部呼叫了base class的 protected 方法
    }
}

```
![[Pasted image 20240718135941.png]]- Class**預設**的`存取修飾詞`是 internal (同一個dll檔 i.e. 專案)

---

### 與物件導向的關聯 (Connection to OOP)

*   **核心原則：封裝 (Encapsulation)**

存取修飾詞是實現**封裝**這個物件導向核心原則的基石。封裝的理念是將物件的內部狀態（資料/欄位）保護起來，只透過一組定義好的、可控的公開介面（方法或屬性）來允許外部存取。

存取修飾詞正是用來定義這個「可見範圍」的工具。例如:
- **`private`**: 將欄位設為私有，確保只有類別內部可以存取，保護了物件的狀態不被外部隨意篡改。
- **`public`**: 將方法或屬性設為公開，作為外部與物件互動的正式管道。

因此，討論存取修飾詞就是討論如何實現封裝，這是物件導向程式設計最基本的概念之一。