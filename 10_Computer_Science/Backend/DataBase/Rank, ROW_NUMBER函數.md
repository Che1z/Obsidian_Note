`RANK()`函數，屬於內建函式，會給予相同數值的資料<mark style="background: #FFB86CA6;">相同的排名</mark>，並跳過接下來的排名數。 如果有多個資料有相同的排序條件，它們會共享同一個排名，但接下來的排名數會被跳過。

``` SQL
SELECT OrderID, CustomerID, OrderDate, RANK() OVER (ORDER BY OrderDate) AS 訂單排名 
FROM Orders;
```

ROW_NUMBER()

``` SQL
SELECT OrderID, CustomerID, OrderDate, ROW_NUMBER() OVER (ORDER BY OrderDate) AS 訂單排名 
FROM Orders;

```

``` SQL
SELECT
    姓名,
    成績,
    ROW_NUMBER() OVER (ORDER BY 成績 DESC) AS RowNumber,
    RANK() OVER (ORDER BY 成績 DESC) AS Rank
FROM
    scores;

```
結果：

姓名   | 成績 | RowNumber | Rank
-------|------|-----------|-----
小明   | 90   |    1      | 1
小李   | 90   |    2      | 1
小華   | 88   |    3      | 3
小紅   | 85   |    4      | 4
