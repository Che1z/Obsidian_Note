允許篩選特定資料，以及執行計算

Select
SelectMany

若是資料是兩層的`List string`
使用`Select`會回傳`list of list string`需要用`2層foreach loop`去處理

```C#
List<List<string>> listOfLists = new List<List<string>> 
{
    new List<string> { "a", "b", "c" },
    new List<string> { "d", "e" },
    new List<string> { "f", "g", "h" }
};

var result = listOfLists.Select(innerList => innerList.ToList()).ToList();

// 需要兩層 foreach 來處理
foreach (var innerList in result)
{
    foreach (var item in innerList)
    {
        Console.WriteLine(item); // 輸出: a, b, c, d, e, f, g, h
    }
}

```
- **`Select`**: 保持原始層次結構，結果是 `List<List<string>>`，需要兩層 `foreach` 來遍歷。


使用`SelectMany`的話，則會回傳`1層list string`這樣只需1層`foreach loop`去處理

```C#
List<List<string>> listOfLists = new List<List<string>> 
{
    new List<string> { "a", "b", "c" },
    new List<string> { "d", "e" },
    new List<string> { "f", "g", "h" }
};

var result = listOfLists.SelectMany(innerList => innerList).ToList();

// 只需要一層 foreach 來處理
foreach (var item in result)
{
    Console.WriteLine(item); // 輸出: a, b, c, d, e, f, g, h
}

```
- **`SelectMany`**: 將所有元素展平，結果是 `List<string>`，只需要一層 `foreach` 來遍歷。