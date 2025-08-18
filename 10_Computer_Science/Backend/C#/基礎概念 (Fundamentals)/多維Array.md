比喻：二維Array（棋盤）、三維Array（魔術方塊）

二維Array寫法：
	數字定義Array大小：
``` csharp
char [,] array = new char [2, 3];

//示意圖
x x x
x x x (Array：2x3)

array[0, 0] = 'A';
array[0, 1] = 'B';
array[0, 2] = 'C';
array[1, 0] = 'D';
array[1, 1] = 'E';
array[1, 2] = 'F';
```
  用{}定義Array內容：
``` csharp
char [,] array2 = new char [,]{
 {'A', 'B', 'C'},
 {'D', 'E', 'F'},
}