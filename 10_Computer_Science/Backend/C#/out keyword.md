兩點存在原因：
1. Method參數預設傳遞方式是「按值傳遞」（pass by value）- 傳遞的是複製數值，而非參數本身
參考影片：[Pass by Value VS Pass by Reference - C# Programming - YouTube](https://www.youtube.com/watch?v=9uTLFbBOgmw&ab_channel=ProfessorSaad)
2. 一個Method只能回傳一個結果，若要回傳複數個結果，此時可以使用outkeyword

沒使用out keyword：
	結果：Count of non positive:200
``` csharp
var numbers = new[] { 10, -8, 2, 12 };
int nonPositiveCount  = 200;

// onlyPositive: Caller
var onlyPositive = GetOnlyPositive(numbers, nonPositiveCount);
foreach (var positiveNumber in onlyPositive)
{
    Console.WriteLine(positiveNumber);
}

Console.WriteLine("Count of non positive:" + nonPositiveCount);
Console.ReadKey();

// Callee
List<int> GetOnlyPositive(int[] numbers, int countOfNonPositive)
{
    countOfNonPositive = 0;
    var result = new List<int>();
    foreach (int number in numbers)
        if (number > 0)
        {
            result.Add(number);
        }
    return result;
}
```
在這個例子中，`nonPositiveCount` 是一個 `int` 類型的基本數據類型。當您將這個變數傳遞給方法 `GetOnlyPositive` 時，實際上是將 `nonPositiveCount` 的值複製了一份傳遞給了方法。
在方法內部修改 `countOfNonPositive` 的值並不影響原始的 `nonPositiveCount`。

這樣的機制使得方法內部對參數的修改不會影響到原始變數，保護了原始變數的值。

使用out keyword：
		結果：Count of non positive:0
``` csharp
var numbers = new[] { 10, -8, 2, 12 };
int nonPositiveCount = 200;

// onlyPositive: Caller
var onlyPositive = GetOnlyPositive(numbers, out nonPositiveCount);
foreach (var positiveNumber in onlyPositive)
{
    Console.WriteLine(positiveNumber);
}

Console.WriteLine("Count of non positive:" + nonPositiveCount);
Console.ReadKey();

// Callee
List<int> GetOnlyPositive(int[] numbers, out int countOfNonPositive)
{
    countOfNonPositive = 0;
    var result = new List<int>();
    foreach (int number in numbers)
        if (number > 0)
        {
            result.Add(number);
        }
    return result;
}
```


out keyword比喻：
	想像你在一家餐廳點了一份外帶，`out` 就像是一個空的「外帶袋」。你事先不知道裝什麼東西，但當餐廳把食物裝進袋子後，你可以把這份外帶袋帶回家，這就是 `out` 在 C# 中的作用。

   具體來說，當你使用 `out` 修飾符聲明一個方法的參數時，這個參數就像是一個「外帶袋」，在方法內部，這個參數會被填充（裝進東西），然後在方法外部你可以取出這個「外帶袋」中的內容。

