Array自身最大問題：尺寸是固定的 （缺乏彈性）
若是要創造不固定尺寸的Array需使用List
```csharp
	int[] numbers = new int [3];
	numbers[0] = 1;
	numbers[1] = 2;
	numbers[2] = 3;
	Console.WriteLine(numbers[^1]); //3 
```
[[Index from end operator]] ：`^` 符號用於表示相對於Array結尾的index。(從末端開始算)
這是在 C# 8.0 中引入的index從結尾計算的語法糖

無需分別定義個別index數值：
```csharp
	int[] numbers = new int []{1, 2, 3}; // {}內被稱為array initializer
	Console.WriteLine(numbers[^1]); //3 
```

不特別定義type：
```csharp
	var[] numbers = new [] {1, 2, 3};
```