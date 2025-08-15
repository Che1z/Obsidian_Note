Distinct, Union, Interset

1.  **Distinct()** - 去除序列中的重複值，並產生一個僅包含唯一值的序列。
```c#
var numbers = new List<int> { 1, 2, 2, 3, 3, 3, 4, 4, 4, 4 }; var distinctNumbers = numbers.Distinct(); 
// 產生的序列為: 1, 2, 3, 4
```
2. **Union()** - 將兩個集合，合併成一個集合 （除去重複值）
``` c#
var set1 = new List<int> { 1, 2, 3 }; 
var set2 = new List<int> { 3, 4, 5 }; 
var unionSet = set1.Union(set2); 
// 產生的序列為: 1, 2, 3, 4, 5
// Note: Concat()：將兩個集合，合併成一個集合 （但不去除重複值）
```
3. **Interset()** - 回傳兩個集合中，重複的值
```c#
var set1 = new List<int> { 1, 2, 3, 4 }; 
var set2 = new List<int> { 3, 4, 5, 6 }; 
var intersectSet = set1.Intersect(set2); 
// 產生的序列為: 3, 4
```