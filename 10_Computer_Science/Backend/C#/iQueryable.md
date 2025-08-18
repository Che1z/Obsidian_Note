# IQueryable<T> 介面

`IQueryable<T>` 是 .NET 中 LINQ（Language Integrated Query）架構的關鍵部分，特別是在與外部資料來源（如資料庫）互動時。它代表一個「尚未執行」的查詢。

---

### 核心概念：查詢的藍圖

您可以將 `IQueryable<T>` 物件想像成一份 **SQL 查詢的藍圖或計畫**。它本身只是一個「查詢的描述」，並未真正執行並從資料庫中抓取資料。

當您撰寫 LINQ to SQL 或 Entity Framework 查詢時，實際上是在建立一個表達式樹（Expression Tree）。這個表達式樹詳細記錄了您想要執行的所有操作，例如篩選（Where）、排序（OrderBy）、投影（Select）等。

**範例：**
```csharp
// 此時，沒有任何資料庫查詢發生
// 'query' 是一個 IQueryable<User> 物件，它儲存了查詢的「意圖」
IQueryable<User> query = db.Users.Where(u => u.Age > 18);
```

在此階段：
- `query` 物件不包含任何使用者資料。
- 應用程式尚未與資料庫進行任何通訊。
- 它只是一個準備好被轉換成 SQL 的查詢結構。

---

### IQueryable 的組成公式

一個常被用來解釋 `IQueryable<T>` 的簡潔公式是：

**`IQueryable<T> = IEnumerable<T> + Expression Tree + Provider`**

這個公式精準地描述了 `IQueryable<T>` 的三個核心組成部分：

1.  **`IEnumerable<T>` (繼承關係):**
    - `IQueryable<T>` 介面繼承自 `IEnumerable<T>`。這意味著任何 `IQueryable` 物件本質上也是一個 `IEnumerable`。(相關筆記: [[IEnumerable]])
    - 這就是為什麼你可以對 `IQueryable` 使用 `foreach` 迴圈。當你這麼做時，就觸發了查詢的「執行」，因為 `foreach` 需要實際的資料來進行迭代。

2.  **Expression Tree (表達式樹):**
    - 這是 `IQueryable` 與 `IEnumerable` 最根本的區別。
    - 當您對 `IQueryable` 撰寫 LINQ 查詢時，您的 C# 程式碼不會被編譯成可執行的指令，而是被轉換成一個名為「表達式樹」的資料結構。
    - 這個樹狀結構「描述」了您的查詢邏輯（例如，哪個欄位要篩選、用什麼條件、如何排序）。因為它是資料，所以可以被程式分析、修改和「翻譯」。

3.  **Provider (LINQ 提供者):**
    - LINQ 提供者是這一切的翻譯官和執行者。例如，Entity Framework 的 SQL Provider 就是一個常見的提供者。
    - 它的工作是：
        - **解析** 表達式樹。
        - 將其 **翻譯** 成目標資料來源的查詢語言（通常是 SQL）。
        - **執行** 該查詢。
        - 將查詢結果包裝成 .NET 物件後返回。

總結來說，當您操作 `IQueryable` 時，您正在建立一個描述查詢的 **表達式樹**，然後由 **LINQ 提供者** 將其翻譯並在遠端資料庫上執行，最後的結果可以像 `IEnumerable` 一樣被迭代。

---

### 延遲執行 (Deferred Execution)

`IQueryable` 的核心特性是 **延遲執行**。這意味著查詢的轉換和執行會被推遲到「真正需要資料」的那一刻。

當您對 `IQueryable` 物件執行以下任何操作時，LINQ 提供者（如 Entity Framework）會將表達式樹轉換為實際的 SQL 查詢，並發送到資料庫執行：

- **迭代集合：**
  - `foreach` 迴圈
- **轉換為集合：**
  - `.ToList()`
  - `.ToArray()`
  - `.ToDictionary()`
- **取得單一元素：**
  - `.FirstOrDefault()`
  - `.Single()`
  - `.First()`
- **執行聚合函數：**
  - `.Count()`
  - `.Sum()`
  - `.Average()`
  - `.Any()`

**範例：**
```csharp
// 建立查詢藍圖
IQueryable<User> query = db.Users
    .Where(u => u.IsActive)
    .OrderBy(u => u.LastName);

// 此時才將 IQueryable 轉換為 SQL 並執行
// SELECT * FROM Users WHERE IsActive = 1 ORDER BY LastName
List<User> activeUsers = query.ToList(); 
```

---

### 與 IEnumerable 的關鍵差異

- **IQueryable：**
  - **執行地點：** 遠端資料來源（如 SQL Server）。
  - **資料流：** 先在資料庫端完成篩選、排序等操作，只將「最終結果」傳回應用程式。效率高，網路傳輸量小。
  - **用途：** 適用於對資料庫或其他遠端服務進行查詢。

- **IEnumerable：**
  - **執行地點：** 應用程式的記憶體中。
  - **資料流：** 將所有資料從資料來源拉到記憶體後，才開始在記憶體中進行篩選和排序。
  - **用途：** 適用於對記憶體中的集合（如 `List<T>`、`Array`）進行操作。 (相關筆記: [[IEnumerable]])
