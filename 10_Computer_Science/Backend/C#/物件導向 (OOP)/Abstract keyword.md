[[interface]]
Abstract keyword算是implicit virtual，可視為base class無法實例化，而只能被derived class覆寫

和Virtual差異：
base class所定義之方法，無法直接使用，而在derived class則『一定』要覆寫，才可使用該方法

``` C#
using System;

// Abstract base class
abstract class Shape
{
    // Abstract method，沒有實際實現
    public abstract double CalculateArea();

    // 一般方法，有實際實現
    public void DisplayArea()
    {
        double area = CalculateArea();
        Console.WriteLine($"Area: {area}");
    }
}

// Derived class：圓形
class Circle : Shape
{
    // 實作基本類別的抽象方法
    public override double CalculateArea()
    {
        double radius = 5.0;
        return Math.PI * radius * radius;
    }
}

// Derived class：矩形
class Rectangle : Shape
{
    // 實作基本類別的抽象方法
    public override double CalculateArea()
    {
        double length = 4.0;
        double width = 6.0;
        return length * width;
    }
}

class Program
{
    static void Main()
    {
        // 不能實例化抽象類別
        // Shape shape = new Shape(); // 這樣會報錯

        // 但可以使用Derived class
        Circle circle = new Circle();
        circle.DisplayArea(); // 輸出：Area: 78.53981633974483

        Rectangle rectangle = new Rectangle();
        rectangle.DisplayArea(); // 輸出：Area: 24
    }
}

```
