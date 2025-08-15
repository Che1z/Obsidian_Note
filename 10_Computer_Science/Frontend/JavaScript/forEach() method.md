forEach method本身為higher order function，因此在()內參數會填入function

forEach()與arrow function協作的語法為：
```js
forEach(element => ...)
forEach((element, index) => ...)

// 若只是放入一個callback function，則語法為:
forEach(callback Fn)
```

NodeList可使用forEach method，HTMLCollection則無法使用