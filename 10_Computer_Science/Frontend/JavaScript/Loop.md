提供一個快速簡潔的方法重複地完成某件事。不同種類的迴圈，本質上都依樣，把一件事重複地做一定的次數。
若將return關鍵字放在loop內部，則循環會馬上停止
常見的Loop：
- While loop
- Do while loop
- For loop

---
For Loop語法：

> for (initialization ; condition ; final expression) {
>   statement
> }

Initialization是循環開始之前的計數器變量聲明(Declare a variable)。
Condition是每次循環迭代之前要評估的表達式(終止條件)，如果此表達式的計算結果為真，則執行statement ，若為假，則執行退出循環並轉到for loop之後的第一條語句。
Final expression：每次循環迭代結束時要執行的程式碼。

若需重複做，且知道要做幾次，就可使用For loop。

---

While Loop語法：

> while (condition) {
>   statement
> }


創造一個循環，只要測試條件為真，就會執行指定語句。

---
Do while loop語法：

> do {
>   statement
> } while ( condition );

Do while loop創建一個循環，該循環執行指定的statement，直到測試條件評估為假。特點在於，先執行語句後評估條件。