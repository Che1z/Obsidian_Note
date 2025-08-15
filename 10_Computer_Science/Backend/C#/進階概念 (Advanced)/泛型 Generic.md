# C# 泛型 (Generic)

泛型（Generic）的概念允許在<mark style="background: #FFB86CA6;">定義類型或方法時使用參數</mark>，以便稍後指定實際的型別。
這樣可以提高程式碼的重用性、靈活性和安全性。

## 泛型的基本概念

泛型透過「型別參數」工作，這些參數是實際型別的預留位置，在使用時才確定具體型別。C# 中常見的泛型形式包括：

- 泛型類別
- 泛型介面
- 泛型方法
- 泛型委派

## 泛型類別

泛型類別允許定義可處理不同型別的資料結構。

```csharp
// 泛型類別宣告
public class Container<T>
{
    private T _item;

    public Container(T item)
    {
        _item = item;
    }

    public T GetItem()
    {
        return _item;
    }

    public void SetItem(T item)
    {
        _item = item;
    }
}

// 使用泛型類別
Container<int> intContainer = new Container<int>(123);
int value = intContainer.GetItem(); // 123

Container<string> stringContainer = new Container<string>("Hello");
string text = stringContainer.GetItem(); // "Hello"
```

## 泛型方法

泛型方法可以獨立於其所在類別接受型別參數。

```csharp
// 非泛型類別中的泛型方法
public class Utilities
{
    // 泛型方法
    public static void Swap<T>(ref T a, ref T b)
    {
        T temp = a;
        a = b;
        b = temp;
    }

    // 泛型方法與多個型別參數
    public static Dictionary<TKey, TValue> CreateDictionary<TKey, TValue>(
        TKey key, TValue value) where TKey : notnull
    {
        return new Dictionary<TKey, TValue> { { key, value } };
    }
}

// 使用泛型方法
int a = 5, b = 10;
Utilities.Swap<int>(ref a, ref b); // 現在 a = 10, b = 5

// 編譯器通常可以推斷型別參數
Utilities.Swap(ref a, ref b); // 無需明確指定 <int>

// 多個型別參數
var dict = Utilities.CreateDictionary("Key", 100); // 建立 Dictionary<string, int>
```

## 泛型介面

泛型介面定義了一組適用於任何型別的操作。

```csharp
// 泛型介面
public interface IRepository<T>
{
    T GetById(int id);
    IEnumerable<T> GetAll();
    void Add(T item);
    void Update(T item);
    void Delete(int id);
}

// 實作泛型介面
public class UserRepository : IRepository<User>
{
    private List<User> _users = new List<User>();

    public User GetById(int id)
    {
        return _users.FirstOrDefault(u => u.Id == id);
    }

    public IEnumerable<User> GetAll()
    {
        return _users;
    }

    public void Add(User item)
    {
        _users.Add(item);
    }

    public void Update(User item)
    {
        // 更新邏輯
    }

    public void Delete(int id)
    {
        _users.RemoveAll(u => u.Id == id);
    }
}
```

## 泛型約束

泛型約束限制可用於型別參數的型別，增加了程式碼的安全性和表達能力。

```csharp
// 常見泛型約束
public class ConstraintExamples<T, U, V>
    where T : class               // T 必須是參考型別
    where U : struct              // U 必須是值型別
    where V : IComparable<V>, new() // V 必須實作 IComparable<V> 介面且具有無參數建構函式
{
    // ...
}

// 實際例子
public class DataProcessor<T> where T : IComparable<T>
{
    public T FindMaximum(T[] items)
    {
        if (items == null || items.Length == 0)
            throw new ArgumentException("陣列不能為空");

        T max = items[0];
        for (int i = 1; i < items.Length; i++)
        {
            if (items[i].CompareTo(max) > 0)
                max = items[i];
        }

        return max;
    }
}
```

### 常見的泛型約束類型

1. `where T : struct` - T 必須是值型別
2. `where T : class` - T 必須是參考型別
3. `where T : new()` - T 必須有公共無參數建構函式
4. `where T : <基底類別名稱>` - T 必須派生自指定的基底類別
5. `where T : <介面名稱>` - T 必須實作指定的介面
6. `where T : U` - T 必須是 U 型別或派生自 U 型別

## .NET 中的泛型集合

.NET 提供了豐富的泛型集合類別：

```csharp
// 常用泛型集合
List<int> numbers = new List<int>() { 1, 2, 3, 4, 5 };
Dictionary<string, int> ages = new Dictionary<string, int>()
{
    { "張三", 25 },
    { "李四", 30 }
};
HashSet<string> uniqueNames = new HashSet<string>() { "張三", "李四", "王五" };
Queue<string> messageQueue = new Queue<string>();
Stack<int> callStack = new Stack<int>();
LinkedList<double> linkedList = new LinkedList<double>();
```

## 協變和逆變

協變（Covariance）和逆變（Contravariance）允許在泛型中使用更靈活的型別轉換。

```csharp
// 協變 (使用 out 關鍵字) - 允許比原始型別更派生的型別
IEnumerable<string> strings = new List<string>();
IEnumerable<object> objects = strings; // 協變

// 逆變 (使用 in 關鍵字) - 允許比原始型別更基礎的型別
Action<object> objectAction = obj => Console.WriteLine(obj);
Action<string> stringAction = objectAction; // 逆變
```

## 泛型與效能

泛型提供型別安全的同時，也帶來效能上的優勢：

1. **避免裝箱和拆箱操作**：對於值型別，使用非泛型集合（如 ArrayList）需要裝箱操作，而泛型集合（如 List<T>）則不需要
2. **提前編譯檢查**：型別錯誤在編譯時就能被發現
3. **最佳化的 IL 代碼**：編譯器為每種使用的型別生成最佳的 IL 代碼

## 泛型的實際應用

泛型在 C# 程式設計中有廣泛的應用：

1. **集合管理**：List<T>, Dictionary<TKey, TValue> 等
2. **資料存取層**：Repository<T> 模式
3. **依賴注入**：IService<T>
4. **LINQ 查詢**：IEnumerable<T> 和 IQueryable<T>
5. **並行和非同步程式設計**：Task<T>

```csharp
// 使用泛型處理非同步操作
public async Task<List<User>> GetAllUsersAsync()
{
    return await _dbContext.Users.ToListAsync();
}

// 使用 LINQ 和泛型
var adults = personList
    .Where(p => p.Age >= 18)
    .OrderBy(p => p.Name)
    .Select(p => new { p.Name, p.Age });
```

## 泛型的限制

使用泛型時也有一些限制需要注意：

1. 不能對泛型參數執行依賴於特定型別的操作，除非透過約束或轉型
2. 泛型參數不能用於靜態欄位或靜態屬性
3. 不能建立泛型型別陣列，如 `new T[10]`（需通過 `Array.CreateInstance` 方法）
4. 不能對型別參數使用 `typeof` 運算子（例如 `typeof(T)`）

泛型是 C# 中功能強大且靈活的特性，能夠顯著提高程式碼的重用性、型別安全性和效能。
