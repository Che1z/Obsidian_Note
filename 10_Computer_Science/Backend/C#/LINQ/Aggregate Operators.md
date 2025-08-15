Min : 回傳最小值

``` C#
//找到陣列的最小值

// 1. 非LINQ寫法
int [] Numbers = {1,2,3,4,5,6,7};

int? result = null;

foreach(int i in Numbers){
  if(!result.HasValue || i < result)
  {
    result = i;
  }
}
Console.WriteLine(result);

// 2. LINQ寫法
int [] Numbers = {1,2,3,4,5,6,7};

int result = Numbers.Min();

Console.WriteLine(result);
```
Max：回傳最大值
Sum：回傳總和
Count：回傳數量
Average：回傳平均 （總和/數量）

Aggregate ：用於在集合上執行累加操作

舉例：
 1. 計算整數陣列的和
``` c#
int[] numbers = { 1, 2, 3, 4, 5 };
int sum = numbers.Aggregate((total, next) => total + next);
Console.WriteLine(sum); // 輸出 15
```

2. 另一種`Overload寫法`，包含`Seed（預設值）`
預設值如下：
`new { PositiveSum = 0, NegativeSum = 0 }`

``` c#
int[] numbers = { -1, 2, -3, 4, -5 };
var result = numbers.Aggregate(new { PositiveSum = 0, NegativeSum = 0 },
    (acc, next) => new
    {
        PositiveSum = next > 0 ? acc.PositiveSum + next : acc.PositiveSum,
        NegativeSum = next < 0 ? acc.NegativeSum + next : acc.NegativeSum
    });
Console.WriteLine($"Positive Sum: {result.PositiveSum}, Negative Sum: {result.NegativeSum}"); // 輸出 "Positive Sum: 6, Negative Sum: -9"

```