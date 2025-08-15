Event表示一個在DOM物件上所發生的事件。
事件的發生通常是由於使用者的操作行為所導致，當某個事件在某個元素上發生時，我們就可以透過撰寫程式碼來讓其做出相對應反應。

addEventListener()可以讓我們在window object, document object以及element object上掛一個事件監聽器。當特定事件發生時，該監聽器就會執行被賦予的function
```js
addEventListener(type, listener);
```
type：事件類別，如click
listener：通常為function或是arrow function expression

所有Event Objects中，最常用到的屬性與方法是：
- target：指向最初觸發事件的DOM物件
- preventDefault()：取消事件的預設行為，不影響事件傳遞
- stopPropagation()：可防止在event bubbling進一步傳播當前事件