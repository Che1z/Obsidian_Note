try, catch, finally語法
``` c#
// try{}內放入，覺得『可能』會有錯誤產生的程式碼
try{

}
// catch{}內程式碼，是當try{}內發生錯誤時執行
catch{

}
// finally{}內程式碼，是不論try{}有無發生錯誤，都會執行
// finally不一定要有
finally{

}
```

一個try block後面，可以接『複數個』catch block，用於處理特定情境

``` c#
try{
        Console.WriteLine("請輸入userinput");
        string userinput = Console.ReadLine();
        int input = int.Parse(userinput);
    }
catch (FormatException ex){
        Console.WriteLine($"FormatException : {ex.Message}");
    }
catch (ArgumentException ex) {
        Console.WriteLine($"ArgumentException：{ex.Message}");
    }

// FormatException、ArgumentException是已定義好的class
```
System. Exception(所有異常的base class)可分為FormatException、ArgumentException

