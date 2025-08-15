  
在 SQL 中，表達式（Expression）是由數值、文字、列名、運算符號等組成的結構，用於計算結果或生成新的值。以下是一些常見的 SQL 運算符和表達式：
1. **數學運算符：**
    
    - 加法：`+`
    - 減法：`-`
    - 乘法：`*`
    - 除法：`/`
    - 取餘數：`%`
    ```SQL
    SELECT salary * 1.1 AS IncreasedSalary FROM Employees;
    ```
    
2. **比較運算符：**
    
    - 等於：`=`
    - 不等於：`<>` 或 `!=`
    - 大於：`>`
    - 小於：`<`
    - 大於等於：`>=`
    - 小於等於：`<=`
    
``` SQL
SELECT ProductName, UnitPrice
FROM Products
WHERE UnitPrice > 50;
```
    
3. **邏輯運算符：**
    
    - AND：`AND`
    - OR：`OR`
    - NOT：`NOT`
    
``` SQL
    SELECT ProductName, UnitsInStock FROM Products 
    WHERE UnitsInStock > 0 AND UnitsInStock < 10;
```
    
4. **字串運算符：**
    
    - 串接字串：`||`（某些資料庫系統）或 `+`
    - 字串長度：`LENGTH()` 或 `LEN()`
    - 字串截取：`SUBSTRING()` 或 `SUBSTR()`
    
``` SQL
SELECT FirstName || ' ' || LastName AS FullName FROM Employees;
```
    
    
5. **函數：**
    
    - SQL 提供了多種內建的函數，如 `COUNT()`、`SUM()`、`AVG()`、`MAX()`、`MIN()` 等。
    
``` SQL
SELECT AVG(salary) AS AverageSalary FROM Employees;
```
---
簡單範例舉例：
``` SQL
SELECT title,(Domestic_sales+Internate_sales)/1000000 As TotalMil
FROM movies as M
LEFT JOIN Boxoffice as B
WHERE M.Id = B.Movie_id;
```
    