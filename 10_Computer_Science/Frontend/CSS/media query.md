兩段式設定，針對不同情境應用不同設定值

舉例：
視窗寬度在800px以上時背景色為黃色，以下則為紅色

> < style> 
 h1{ 
   background-color: yellow;
 }
 
 @media screen and (max-width: 800px){
> h1{
>     background-color:red;
>   }
> }
> < /style>
