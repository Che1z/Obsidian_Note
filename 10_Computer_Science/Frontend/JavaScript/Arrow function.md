語法：

```
() => expression
param => expresssion
(para1, para2, ...) => expression
param => {return expression}
```

1. 注意在expression處，沒有使用大括號時會自動return expression
2. 在使用大括號時，需手動撰寫return，最終才會回傳值
3. 若只有１個parameter，則不需加上括號()也可執行
4. 若有０個或是２個以上的parameters，則一定要加括號
5.  Arrow function沒有this keyword綁定，不應該在objects的methods中使用

---
[[forEach() method]]