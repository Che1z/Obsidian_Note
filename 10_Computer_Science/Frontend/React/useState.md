### 什麼是State?
<p>State generally refers to data or properties that need to be tracking in an application.</p>
---

useState 是被用來加入一些基礎的變數狀態。
useState 會回傳一組數值：目前 state 數值和一個可以更新 state 的方法，舉例如下：

> const [count, setCount] = React.useState(0);
> count為變數(設定初始值為0)、setCount則為使用方法

定義透過 setCount 方法可以改變 count 的值：
>  setCount(count + 1)


實際例子：
![[Screenshot 2023-08-14 at 9.36.51 PM.png]]