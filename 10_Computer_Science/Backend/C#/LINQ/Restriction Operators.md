WHERE語法

2種Overload語法
``` C#

// 僅使用元素本身來過濾集合
1. [Where<TSource>(IEnumerable<TSource>, Func<TSource,Boolean>)]

// 過濾條件基於元素本身和它在集合中的索引
2. [Where<TSource>(IEnumerable<TSource>, Func<TSource,Int32,Boolean>)]
```


舉例：
```c#

// 寫法1
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();

foreach (var number in evenNumbers)
{
    Console.WriteLine(number); // 輸出 2, 4
}

// 寫法2
List<string> words = new List<string> { "apple", "banana", "cherry", "date" };
var wordsWithEvenIndices = words.Where((word, index) => index % 2 == 0).ToList();

foreach (var word in wordsWithEvenIndices)
{
    Console.WriteLine(word); // 輸出 apple, cherry
}


```