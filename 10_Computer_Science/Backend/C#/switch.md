		使用switch語法，從眾多條件中，挑選一部分程式碼執行

default語法為else意思，當沒有任何條件符合時，即會執行

```csharp
int day = 4;
switch (day) 
{
  case 1:
    Console.WriteLine("Monday");
    break;
  case 2:
    Console.WriteLine("Tuesday");
    break;
  case 3:
    Console.WriteLine("Wednesday");
    break;
  case 4:
    Console.WriteLine("Thursday");
    break;
  case 5:
    Console.WriteLine("Friday");
    break;
  case 6:
    Console.WriteLine("Saturday");
    break;
  case 7:
    Console.WriteLine("Sunday");
    break;
  default:
    Console.WriteLine("Looking forward to the Weekend.");
    break;
```
}
// Outputs "Thursday" (day 4)
```