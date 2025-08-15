`TOP (SQL Server), LIMIT (MySQL), ROWNUM (Oracle)` 這些語法其實都是同樣的功能，都是用來限制您的`SQL`查詢語句最多只影響幾筆資料，而不同的語法則只因不同的資料庫實作時採用不同的名稱。

`Top Syntax`：
``` SQL
SELECT TOP number|percent table_column1, table_column2... 
FROM table_name;
```
可以用`絕對數量(number)或比例(percent)`來限制上限 

例子：

原檔：

|C_Id|Name|City|Address|Phone|
|---|---|---|---|---|
|1|張一|台北市|XX路100號|02-12345678|
|2|王二|新竹縣|YY路200號|03-12345678|
|3|李三|高雄縣|ZZ路300號|07-12345678|
|4|陳四|台北市|AA路400號|02-87654321|

若只要抓取前兩筆資料的話

絕對數量
```sql
SELECT TOP 2 * 
FROM customers;
```
或是比例
```sql
SELECT TOP 50 PERCENT * 
FROM customers;
```