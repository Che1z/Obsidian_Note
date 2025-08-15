`Select`：搜尋、查詢以及撈取
``` SQL
Select column1, column2
From table_name
where table_ID < 100;

Select *
From table_name
where table_name = 'Tag';

-- Select：選擇要檢索的列
-- From：要檢索資料表位置
-- Where：篩選條件
-- Note : * 為顯示全部、字串要使用單引號(')包覆
```

`Insert`...`into`：新增
``` SQL
-- 基本 INSERT 語法
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);

-- 範例
INSERT INTO Customers (FirstName, LastName, Email)
VALUES ('John', 'Doe', 'john.doe@example.com');

```

`Delete`：刪除
``` SQL
-- 基本 DELETE 語法
DELETE FROM table_name
WHERE condition;

-- 範例
DELETE FROM Customers
WHERE CustomerID = 1001;

```

`Update`... `Set`：修改、更新 
``` SQL
-- 基本 UPDATE 語法
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

-- 範例
UPDATE Products
SET Price = 20.99
WHERE ProductID = 101;

-- UPDATE：用於修改表中的現有資料行。
-- SET：用於指定要修改的列和新值。
-- WHERE：子句用於篩選要更新的資料行。
```