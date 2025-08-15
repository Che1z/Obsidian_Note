三種：Range, Repeat, Empty

1. **Range()** - 產生特定區間的序列整數。
``` c#
csharp var rangeSequence = Enumerable.Range(1, 10); 
// 產生的序列為: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 
``` 

2. **Repeat()** - 產生含特定重複值的序列。 
``` c#
csharp var repeatSequence = Enumerable.Repeat("Hello", 5);
// 產生的序列為: "Hello", "Hello", "Hello", "Hello", "Hello"
```

3. **Empty()** - 回傳特定類別的空序列。 
```c#
csharp var emptySequence = Enumerable.Empty<int>(); 
// 產生的序列為: (空的序列) 
```
