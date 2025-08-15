
`Linear search (線性搜尋)`
- Big O: O(n) - 最壞情况下需要查找整個Array
- Omega: Ω(1) - 最好情况下第一個元素就找到

`Binary search (二元搜尋)` 
- Big O: O(log n) - 每次查找都將搜尋範圍減半
- Omega: Ω(1) - 最好情况下,中間元素就找到

[[時間複雜度]]

`Sorting`

`Selection sort : 每一次執行循環找最小值並記錄，因此每一次就可以找到最小值`
	時間效率： (n) * (n-1) / 2 => O(n ^ 2);
	不論何種情況，都是一樣的時間複雜度 （無法提早結束）

`Bubbling sort : 左右比較，一次循環就可以找到最大值`
	時間效率： (n-1) * (n-1)  => O(n ^ 2); 
	總共需要`n-1`個循環，每個循環裡頭也是`n-1`次的循環 
	
	提早結束：
	但如果整個小循環內，沒有交換的話，即代表已經成功排序
	因此Omega: Ω(n) - 最好情况下,查看整個集合一次即完成

`Recursion : Function自己呼叫自己

`Merge sort : 相較於Selection和Bubbling更有效率`
- 時間複雜度在所有情況下都是 O(n log n) - n * log2n
- 在最好情況下Bubble Sort 的 O(n) 可能比 Merge Sort 的 O(n log n) 更好




