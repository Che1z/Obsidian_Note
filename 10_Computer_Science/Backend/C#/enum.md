enum是列舉，宣告時不需要指出型態是什麼，其每一個元素的底層型態都是`int`

``` c#
enum Days
{
    Sunday,    // 0
    Monday,    // 1
    Tuesday,   // 2
    Wednesday, // 3
    Thursday,  // 4
    Friday,    // 5
    Saturday   // 6
}
```

`Days` 列舉定義了一組代表星期的常數。每個元素的值是按照它們在列舉中的位置（從 0 開始）依序遞增的整數。你可以使用列舉元素的名稱來表示相應的整數值，例如 `Days.Monday` 代表的整數值是 1。

可更改數值，從1開始計算
``` C#
enum Days
{
    Sunday = 1,    // 從 1 開始計算
    Monday,        // 預設情況下，Monday 將是 2
    Tuesday,       // 3
    Wednesday,     // 4
    Thursday,      // 5
    Friday,        // 6
    Saturday       // 7
}
```