熱門資料庫：`NewtonSoft.Json`，安裝方式要到NuGet Package上尋找（類似於extension）

貼上Data：Visual Studio IDE可以選擇將資料以`JSON Class`的格式貼上
資料處理：
1. 序列化：將`JSON`資料轉變成`String`(`Stringify`)
```c#
string output = JsonConvert.SerializeObject(Object變數)
```
2. 反序列化：將資料轉變成`目標類型`（物件化）
``` C#
目標Class變數 output = JsonConvert.DeserializeObject<Class變數>(jsonString);
```
在反序列化時，你需要提供 JSON 字串（`jsonString`），以及你希望反序列化的指定類型 C# 物件`Class變數`）。這樣才能將 JSON 資料還原為對應的 C# 物件。

---
舉例：
``` C#
// 先建立Class
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

// 使用Newtonsoft.Json方法
using Newtonsoft.Json;

class Program
{
    static void Main()
    {
        // 實例化一個 Person 對象
        Person person = new Person
        {
            Name = "John Doe",
            Age = 30
        };

        // 使用 Newtonsoft.Json.JsonConvert 進行序列化
        string jsonString = JsonConvert.SerializeObject(person);

        // 輸出序列化後的 JSON 字串
        Console.WriteLine(jsonString);
    }
}
```

