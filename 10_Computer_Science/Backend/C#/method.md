名稱要大寫開頭，結尾不得有;
建議命名以『動詞』做為開頭
若method為non-void，則必須確保在所有情況下都會return value;


- TryParse： 先看userInput Parse結果，若是成功再回傳第二個參數數值(parsingResult值)
```csharp
//Try parsing
bool isParsingSuccess;
Console.WriteLine("Enter a number: ");
var userInput = Console.ReadLine();
isParsingSuccess = int.TryParse(userInput, out int parsingResult);
if (isParsingSuccess) {
    Console.WriteLine($"Parsing result: {parsingResult}");
}
```

- DateTime.TryParseExact：以下為參數介紹
1. **string s**: 要解析的日期和時間的字串。
2. **string format**: 字串表示的日期和時間的格式。這個參數用來指定 `s` 的格式。
3. **IFormatProvider provider**: 提供格式化資訊的物件，通常可以設為 `null`，表示使用當前文化（CurrentCulture）。
4. **DateTimeStyles styles**: 指定如何解釋日期和時間值的樣式。常見的值包括 `None`、`AssumeLocal`、`AssumeUniversal` 等。`None` 表示不使用額外的樣式。
5. **out DateTime result**: 如果轉換成功，這個參數會包含轉換後的 `DateTime` 物件；如果轉換失敗，這個參數會被設為 `DateTime.MinValue`。
```c#
Console.WriteLine("請輸入時間(格式HH:MM)");
string userInput = Console.ReadLine();
// null，表示使用當前文化（CurrentCulture） 
if (DateTime.TryParseExact(userInput, "HH:mm", null, System.Globalization.DateTimeStyles.None, out DateTime time))
{
	Console.WriteLine($"{time.Hour}點{time.Minute}分"); ;
}
else
{
    Console.WriteLine("輸入格式錯誤");
}
```


- ToString ：

ToString("F2")`中的 "F2" 是一種自訂格式化字符串，其中 "F" 代表 "Fixed-point"，而 "2" 代表要顯示的小數點位數。

此格式是用於將數字按照固定小數點格式進行格式化。其他常見的自訂格式化字符串包括：

- "C"：貨幣格式。
- "D"：十進位整數格式。
- "E"：科學計數法格式。
- "N"：數字格式，包含千位分隔符。
- "P"：百分比格式。
``` C Sharp
double number = 1234.5678;

string currencyFormat = number.ToString("C"); // 貨幣格式
Console.WriteLine(currencyFormat); // Output: "$1,234.57"

string decimalFormat = number.ToString("D"); // 十進位整數格式
Console.WriteLine(decimalFormat); // Output: "1235"

string scientificFormat = number.ToString("E"); // 科學計數法格式
Console.WriteLine(scientificFormat); // Output: "1.234568E+003"

string numberFormat = number.ToString("N"); // 數字格式
Console.WriteLine(numberFormat); // Output: "1,234.57"

string percentFormat = (number / 100).ToString("P"); // 百分比格式
Console.WriteLine(percentFormat); // Output: "1234.57%"

```