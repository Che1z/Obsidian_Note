標準的`Query Operators`是作為`IEnumerable<T> interface`的擴充方法
因此只要是`IEnumerable`或`IQueryable`的資料類型，都可以使用`LINQ Query`

LINQ 查詢可以應用於任何實現了 `IEnumerable<T>` 或 `IQueryable<T>` 介面的資料集合

[擴充方法解釋](https://www.youtube.com/watch?v=VkrKNXscoto&list=PL6n9fhu94yhWi8K02Eqxp3Xyh_OmQ0Rp6&index=3&ab_channel=kudvenkat)
簡介：在既有類別中增加方法（不新增繼承類別，重新編譯，改變既有類別）
擴充方法是特殊形式的`static method`

運算子分類
LINQ Standard Query Operators分類：
[[LINQ Operators categories]]

查詢分類：
1. Deferred or Lazy Operators：不會立即執行，Select, Where, Take, Skip......
2. Immediate or Greedy Operators：立即執行，Count, Average, Min, Max, ToList