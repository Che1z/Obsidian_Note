1. While loop （先檢查條件，再執行）因此可能都不執行
變數需要先宣告，不能寫在括號內
```csharp
var loopNumber = 0;
//當while()內條件符合時，執行程式碼
while (loopNumber < 10) { 
    loopNumber++;
    Console.WriteLine(loopNumber);
};
Console.WriteLine("Loop finished.");
```

2. do while loop (先執行再檢查條件）至少會執行一次
```csharp
Console.WriteLine("Please enter the input");
var userinput = Console.ReadLine();
do
{
    Console.WriteLine($"Userinput is: {userinput}");
}
while (userinput.Length > 10);
```

3. for loop 內部分成（initialize, condition, iteration），條件達成後才會執行{}內程式碼
```csharp
for (int i = 0; i < 5; i++) {
    Console.WriteLine("Loop round:" + i);
}
	```
	

4. foreach loop

語法：

``` csharp
/* 
  foreach (type variableName in arrayName) 
{
  // code block to be executed
} 
*/

foreach(int num in array){
  Console.WriteLine(num);
}
```