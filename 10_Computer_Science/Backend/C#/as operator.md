``` C#
Cheddar cheddar = (Cheddar) ingredient; // Explicit conversion
Cheddar cheddar = ingredient as Cheddar // As operator
```

Explicit conversion則可用於任何類別轉換，但一但失敗就會直接回傳錯誤
``` C#
double doubleValue = 10.5;
int intValue = (int)doubleValue; // 顯式轉換，可能會有資料損失

Console.WriteLine(intValue); // 結果是 10

```

As operator特點，轉變失敗時會回傳null，而非錯誤 (但只限定使用於nullable varible)

``` C#
int number = ingredient as Cheddar //此程式碼就會錯誤，因為int為non-nullable variable
```