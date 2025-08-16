C#變數（盒子）具有專一性，若是決定好盒子類型，後續不得更改
``` csharp
int box = "intonly"; //explictly命名方式
box = "change"; //box只能輸入字符串
```
上方是宣告(declaration)即定義內容類型，若要讓程式從賦予值決定變數類型，可使用var

``` csharp
var box = "intonly"; //implicitly命名方式
box = "change"; 
```

命名規則：
1. 有保留字設計（可用@bypass）
2. 名字可包含文字、數字、底線（但第一個字不可為數字）
3. 大小寫有別