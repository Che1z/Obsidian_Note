Take：回傳特定數量的資料
Skip：忽略特定數量的資料

TakeWhile：回傳符合條件的資料
SkipWhile：忽略符合條件的資料
```C#
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.SkipWhile(n => n < 4); // 返回 {4, 5}

```
