在`Select`查詢語法中，我們可以透過`DISTINCT`來過濾重複資料

`DISTINCT Syntax`

```SQL
SELECT DISTINCT table_column1, table_column2... 
FROM table_name;
```

例子：

|C_Id|Name|City|Address|Phone|
|---|---|---|---|---|
|1|張一|台北市|XX路100號|02-12345678|
|2|王二|新竹縣|YY路200號|03-12345678|
|3|李三|高雄縣|ZZ路300號|07-12345678|
|4|陳四|台北市|AA路400號|02-87654321|
使用`DISTINCT`
``` SQL
SELECT DISTINCT City 
FROM customers;
```

結果為：

|City|
|---|
|台北市|
|新竹縣|
|高雄縣|

原本資料表的 City 欄位中有<mark style="background: #FFF3A3A6;">兩個重複值</mark>台北市，可是我們只想知道有哪幾個縣市有顧客而已，故我們使用 DISTINCT 關鍵字來限制僅取出欄位中 "不相同" 的值。

當`SELECT`複數個欄位時：
	若SELECT DISTINCT 後面有指定兩個以上的欄位，則要符合所有欄位值皆同樣重複的情況下該筆資料才會被捨棄。
	若只有其中一個欄位值相同但其它欄位值並不同，則仍會取出該筆資料。
