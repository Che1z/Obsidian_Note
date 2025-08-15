使用`SELECT`查詢資料時，可透過`ORDER BY`排序資料，其方式有由小至大（`預設：Ascending`）或由大至小（`Descending`）兩種。


`ORDER BY Syntax`
``` SQL
SELECT table_column1, table_column2... F
ROM table_name ORDER BY column_name1 ASC|DESC, column_name2 ASC|DESC...
```

例子：

|E_Id|Name|Title|
|---|---|---|
|1|Allen|crew|
|2|Tom|manager|
|3|Chris|crew|
|4|Bill|crew|
```sql
SELECT * 
FROM employees ORDER BY Title ASC, Name DESC;
```
也可以改寫成
```sql
SELECT * FROM employees ORDER BY 3 ASC, 2 DESC;
```
因為：`SELECT關鍵字`後的第一個欄位 (table_column1) 為 1，第二個欄位 (table_column2) 則為 2


結果如下：

|E_Id|Name|Title|
|---|---|---|
|3|Chris|crew|
|4|Bill|crew|
|1|Allen|crew|
|2|Tom|manager|
