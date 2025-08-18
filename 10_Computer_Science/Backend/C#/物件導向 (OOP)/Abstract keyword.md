# C# 抽象類別 (Abstract Class)

`abstract` 關鍵字是 C# [[物件導向 (OOP)]] 中用來實現**抽象化 (Abstraction)** 的核心工具。它用於定義不能被[[基礎概念 (Fundamentals)/class|實例化]]的類別，並作為其他[[Inheritance|衍生類別 (Derived Class)]]的基底藍圖。

---

## 核心概念

抽象類別是一個不完整的類別，它作為一個「合約」或「範本」，定義了一組相關類別共有的成員和必須實現的功能。

- **定義藍圖**: 一個抽象類別 (`abstract class`) 為一群相關的子類別定義了一個共通的「概念」。
- **強制實作**: 抽象方法 (`abstract method`) 在父類別中沒有實作，但強制所有[[Inheritance|繼承]]它的子類別都必須提供自己的實作版本（使用 `override`）。

---

## 主要特性

- **不可實例化**: 您不能使用 `new` 關鍵字建立抽象類別的實例。
- **可包含實作**: 抽象類別可以同時包含**抽象成員**（沒有實作的方法、屬性等）和**具體成員**（有完整實作的方法、屬性等）。
- **繼承**: 抽象類別必須被繼承，由其非抽象的衍生類別來提供所有抽象成員的實作。

---

## `abstract` vs. virtual

| 特性       | `abstract` 方法               | virtual 方法                      |
| :------- | :-------------------------- | :------------------------------ |
| **實作**   | 在基底類別中**沒有**實作，只有宣告。        | 在基底類別中**有**預設實作。                |
| **覆寫**   | 衍生類別**必須**使用 `override` 覆寫。 | 衍生類別**可以**選擇性地使用 `override` 覆寫。 |
| **所在類別** | 只能在 `abstract class` 中宣告。   | 可以在任何非 `sealed` 的類別中宣告。         |

---

## `abstract class` vs. interface

抽象類別和介面都用於實現抽象化，但有關鍵區別：

| 特性       | `abstract class`                                       | interface                                           |
| :------- | :----------------------------------------------------- | :-------------------------------------------------- |
| **成員實作** | 可以包含已實作的成員和未實作的抽象成員。                                   | 所有成員都不能有實作（C# 8.0 後可有預設實作，但非主流用法）。                  |
| **繼承**   | 一個類別只能繼承**一個**抽象類別。                                    | 一個類別可以實作**多個**介面。                                   |
| **成員類型** | 可以包含欄位、建構子、解構子等。                                       | 只能包含方法、屬性、事件、索引子。                                   |
| **設計目的** | 用於定義一組「is-a」關係的物件藍圖（例如：`Car` is an `AbstractVehicle`）。 | 用於定義一個類別「can-do」的功能合約（例如：`Bird` can-do `IFlyable`）。 |

---

## 範例程式碼

```C#
using System;

// 抽象基底類別
abstract class Shape
{
    // 抽象方法，沒有實作
    public abstract double CalculateArea();

    // 一般方法，有完整實作
    public void DisplayArea()
    {
        double area = CalculateArea();
        Console.WriteLine($"Area: {area}");
    }
}

// 衍生類別：圓形
class Circle : Shape
{
    // 必須實作基底類別的抽象方法
    public override double CalculateArea()
    {
        double radius = 5.0;
        return Math.PI * radius * radius;
    }
}

// 衍生類別：矩形
class Rectangle : Shape
{
    // 必須實作基底類別的抽象方法
    public override double CalculateArea()
    {
        double length = 4.0;
        double width = 6.0;
        return length * width;
    }
}
```

---
### 與物件導向的關聯 (Connection to OOP)

*   **核心原則：抽象 (Abstraction) 與 繼承 (Inheritance)**

`abstract` 關鍵字是實踐**抽象**這個物件導向核心原則的主要工具。抽象的目的是隱藏複雜的實作細節，只向上層或使用者呈現必要的功能介面。

- **定義藍圖**: 一個抽象類別（`abstract class`）為一群相關的子類別定義了一個共通的「概念」或「藍圖」。它本身不能被實例化。
- **強制實作**: 抽象方法（`abstract method`）在父類別中沒有實作，但強制所有繼承它的子類別都必須提供自己的實作版本（使用 `override`）。

這種機制與**繼承**緊密結合，建立了一個清晰的層級結構，並透過**多型 (Polymorphism)** 讓不同的子類別物件能以自己的方式回應相同的方法呼叫。因此，`abstract` 是物件導向設計中不可或缺的一環。
