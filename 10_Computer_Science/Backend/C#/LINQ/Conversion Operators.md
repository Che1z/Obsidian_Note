ToList：將所有`Collection itmes`轉成`List`回傳
ToArray：將所有`Collection itmes`轉成`Array`回傳
ToDictionary：將所有`Collection itmes`轉成`Dictionary`回傳
ToLookup：將所有`Collection itmes`轉成`Lookup`回傳
Note: 
	Dictionary v.s. Lookup
	兩者都是Key-Value Pair
	Dictionary的Key不可重複，Lookup則可以

Cast：將`Collection`裡頭的`item`轉成特定Type
	若是無法順利轉成，就會丟`Exception error`
OfType：只回傳特定類型的`item`

### AsEnumerable

- **用途**：`AsEnumerable` 將資料從查詢上下文轉換為 `IEnumerable<T>`，這意味著後續的操作會在客戶端進行。
- **應用場景**：適用於需要在內存中操作資料的情況。例如，在 LINQ 查詢中，當你希望強制後續的操作在客戶端進行，而不是在資料庫中執行時，可以使用 `AsEnumerable`。
- **行為**：一旦使用 `AsEnumerable`，後續的 LINQ 查詢將不再被轉換為 SQL 查詢，而是在內存中執行。
```C#
var query = dbContext.Users
    .Where(u => u.IsActive)
    .AsEnumerable()
    .Where(u => SomeClientSideMethod(u));

var result = query.ToList();

```
只有 `Where(u => u.IsActive)` 會被轉換為 SQL 查詢，並在資料庫中執行。`AsEnumerable` 後的 `Where(u => SomeClientSideMethod(u))` 會在客戶端內存中執行。

AsEnumerable能將`Query`拆分成兩部分
	Inside Part ：執行`LINQ-to-SQL`
	Outside Part：執行`LINQ-to-Objects`




### AsQueryable

- **用途**：`AsQueryable` 將資料從 `IEnumerable<T>` 轉換為 `IQueryable<T>`，這意味著後續的操作可以被轉換為 SQL 查詢並在資料庫中執行（假設是來自 EF 或其他 ORM）。
- **應用場景**：適用於希望在資料庫中進行更多查詢操作的情況。例如，當你有一個 `IEnumerable<T>` 集合並希望利用資料庫的查詢能力來執行複雜的操作時，可以使用 `AsQueryable`。
- **行為**：使用 `AsQueryable` 後，後續的 LINQ 查詢會被轉換為 SQL 查詢並在資料庫中執行（如果最初的來源支持）。
```C#
var list = new List<User>
{
    new User { Id = 1, IsActive = true },
    new User { Id = 2, IsActive = false }
};

var query = list.AsQueryable()
    .Where(u => u.IsActive)
    .Select(u => new { u.Id, u.IsActive });

var result = query.ToList();
```

在這個範例中，`AsQueryable` 將 `list` 轉換為 `IQueryable<T>`，然後後續的 `Where` 和 `Select` 操作可以在資料庫中執行（如果 `list` 來自於資料庫查詢）。

### 總結

- **AsEnumerable**：將資料轉換為 `IEnumerable<T>`，強制後續操作在客戶端內存中進行。適用於需要在內存中操作資料的情況。
- **AsQueryable**：將資料轉換為 `IQueryable<T>`，允許後續操作在資料庫中進行。適用於希望利用資料庫查詢能力進行操作的情況。