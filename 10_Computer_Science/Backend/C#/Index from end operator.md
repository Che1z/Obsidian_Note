屬於語法糖，語法(＾)
從C# 8.0開始新增功能，目的在於選擇index時，可快速從末端index選取

``` csharp
int[] numbers = { 1, 2, 3, 4, 5 };
int lastElement = numbers[^1];  // 得到最後一個元素，即 5
int secondToLast = numbers[^2]; // 得到倒數第二個元素，即 4
```