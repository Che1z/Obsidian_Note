```csharp
// <>中填入集合中元素的型別
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
```
也可以創立一個空List
``` csharp
List<int> numbers = new List<int>{};
```

List自身長度要用Count查看，而非用Length

```c#
Constructor : [List<T>(IEnumerable<T>)]
//意思是rowDat這個IEnumberable數據，儲存在List中，變成以List形式儲存
  List<string> rowData1 = new List<string>(rowData); 
  
//意思是rowData2裡頭的第一個元素，為rowData這個數據  
  List<string> rowData2 = new List<string>{$"{rowData}"}; 
  Console.WriteLine(rowData2.Count); // 1
```