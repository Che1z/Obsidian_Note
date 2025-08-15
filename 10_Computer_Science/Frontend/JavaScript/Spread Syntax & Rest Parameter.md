Spread Syntax：

1. 允許在需要0個或多個『參數』的地方，擴展array內部的元素
可複製Array
```
myFunction(a, ...iterableObj, b)
// 執行function
function sum(x, y, z, a, n){
  return x + y + z + a + n;
}

let arr = [1, 2, 3];
console.log(sum(10, ...arr, 5))

``` 
2. 允許在需要0個或多個『元素』的地方，擴展array內部的元素
```
[1, ...iterableObj, '4', 'five']
```

Rest Parameter：
用法和Spread Syntax相似，主要差異在於使用時機(Function definition時使用)
```
//Note: Args = Arguments
function f(a, b, ...theArgs){
  //...
}

function sum(...theArgs){
  console.log(theArgs)
}

sum(1, 2, 3, 4, 5) // [1, 2, 3, 4, 5]（Args會被壓縮成一個Array）
```