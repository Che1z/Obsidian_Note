撰寫方法為：
```js
function (parameter 0, ... parameterN){
  statement
}

```

和一般的function declaration差在不需賦予function名稱

用途可用於以下三種情況：
1. 將函式賦值給變數：創建一個未命名的Function，再將此Function放置於其他變數內，做後續使用
2. 當作Higher order function的callback function使用
> const button = document.querySelector('button'); 
> button.addEventListener('click', function () { 
>   alert('按鈕被點擊了！'); 
> });
3. 使用IIFE：
> (function () { 
> const localVar = '我是局部的！'; 
> console.log(localVar); 
> })(); // 輸出："我是局部的！"