例外狀況是用來表示執行程式時所發生的錯誤。 建立描述錯誤的Exception Object
``` c#
   static string testFunction()
    {
        Console.WriteLine("請輸入數字");
        string input = Console.ReadLine();
        if (int.TryParse(input, out int result))
        {
            return "輸入:" + Convert.ToString(result);
        }
        throw new Exception("尚未輸入數字");
    }
```

上述方法回傳值型別設定為string，因此在所有情境下都需要回傳string值，若是要針對非string的情境，就可透過throw Exception執行