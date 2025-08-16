
String builder用處在於String manipulation，若是使用既有class定義的方法來處理string
每一次處理完的string都會消耗記憶體，而builder則是針對處理字串這個單一物件去處理

因此當遇到：添加、刪減、替換時，建議使用string builder

此class定義在System.Text namespace裡頭（非System namespace）

```c#
StringBuilder rowHtml = new StringBuilder();
rowHtml.Append("<tr>"); // 用於在字串的尾部添加內容，
rowHtml.Insert(0, "test"); //在特定位置，添加特定文字
```

