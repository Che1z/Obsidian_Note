# IEnumerable<T> 介面

`IEnumerable<T>` 是 .NET 集合框架的基礎。它提供了一個簡單、通用的方式來「迭代」（遍歷）一個序列（或集合）中的所有項目。

---

### 核心概念：記憶體中的序列

您可以將 `IEnumerable<T>` 物件看作是一個 **記憶體中的資料序列**。它代表一個已經存在於應用程式記憶體中的集合，您可以對它進行一次性的、唯讀的、向前移動的遍歷。

所有常見的 .NET 集合（如 `List<T>`、`Array`、`Dictionary<TKey, TValue>`）都實作了 `IEnumerable<T>` 介面。

**範例：**
```csharp
// 建立一個 List<string>，它本身就是一個 IEnumerable<string>
List<string> names = new List<string> { "Alice", "Bob", "Charlie" };

// 使用 foreach 迴圈遍歷這個 IEnumerable
// 這是 IEnumerable 最常見的用法
foreach (string name in names)
{
    Console.WriteLine(name);
}
```

---

### LINQ to Objects

當您對 `IEnumerable<T>` 使用 LINQ 方法時，您使用的是 **LINQ to Objects**。這意味著所有的查詢操作（如 `Where`, `OrderBy`, `Select`）都在應用程式的記憶體中執行。

**延遲執行 (Deferred Execution) in IEnumerable:**
`IEnumerable` 上的許多 LINQ 方法也支援延遲執行，但其機制與 `IQueryable` 完全不同。(相關筆記: [[iQueryable]]) 它的執行被推遲到「迭代開始」時，但所有操作都在記憶體中發生。

**範例：**
```csharp
List<Product> products = GetAllProductsFromDatabase(); // 假設這返回 List<Product>

// 1. GetAllProductsFromDatabase() 執行，從資料庫載入「所有」產品到記憶體
// products 現在是一個 IEnumerable<Product>

// 2. .Where() 和 .OrderBy() 並未立即執行。
// 它們建立了一個迭代器，該迭代器知道如何在需要時執行篩選和排序。
IEnumerable<Product> cheapProducts = products
    .Where(p => p.Price < 100)
    .OrderBy(p => p.Name);

// 3. 當 foreach 開始時，.Where() 和 .OrderBy() 才在「記憶體中」對 products 集合執行
foreach (Product p in cheapProducts) 
{
    Console.WriteLine(p.Name);
}
```
這個過程的關鍵是，**所有**產品資料都先被拉到記憶體中，然後才進行篩選。如果資料庫中有數百萬筆產品，這會消耗大量記憶體和網路頻寬。

---

### 與 IQueryable 的關鍵差異

- **IEnumerable：**
  - **執行地點：** 應用程式的記憶體中 (Client-Side)。
  - **資料流：** 先將資料從來源載入記憶體，然後在記憶體中處理。對於大數據集可能效率低下。
  - **用途：** 適用於對已經存在於記憶體中的集合進行操作。

- **IQueryable：**
  - **執行地點：** 遠端資料來源（如 SQL Server）(Server-Side)。
  - **資料流：** 將查詢指令（如 SQL）發送到遠端執行，只接收最終結果。效率高，適合處理大數據集。
  - **用途：** 適用於對資料庫或其他可查詢的遠端服務進行高效查詢。 (相關筆記: [[iQueryable]])
