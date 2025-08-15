# C# 元數據（Metadata）

元數據（Metadata）是描述其他資料的資料，可以理解為「關於資料的資料」。
在 C# 和 .NET 中，元數據是一種強大的機制，用於描述程式集、型別、成員等的特性和行為。

## 元數據的基本概念

在 .NET 框架中，元數據被內嵌在組件（Assembly）中，包含關於型別、方法、屬性等的詳細描述。
這些元數據使得 .NET 程式擁有自我描述的能力，支持反射、序列化、動態載入等進階功能。

## C# 中的元數據形式

### 1. 屬性（Attribute）

屬性是 C# 中最常見的元數據形式，允許開發者將宣告性訊息附加到程式碼上。

```csharp
[Obsolete("此方法已過時")]
public void OldMethod() { }

[Serializable]
public class Customer { }
```

### 2. XML 文件註釋

XML 文件註釋提供了一種為代碼添加文檔的方式，這些註釋會被編譯為獨立的 XML 文檔，供 IDE 和文檔生成工具使用。

```csharp
/// <summary>
/// 計算兩個數值的總和
/// </summary>
/// <param name="a">第一個加數</param>
/// <param name="b">第二個加數</param>
/// <returns>兩數之和</returns>
public int Add(int a, int b)
{
    return a + b;
}
```

### 3. 反射相關元數據

.NET 透過反射 API 公開了豐富的元數據，這些元數據描述了型別的結構和行為。

```csharp
// 獲取型別的元數據
Type type = typeof(Customer);
Console.WriteLine($"型別名稱: {type.Name}");
Console.WriteLine($"是否為類別: {type.IsClass}");
Console.WriteLine($"組件: {type.Assembly.FullName}");

// 獲取方法的元數據
MethodInfo[] methods = type.GetMethods();
foreach (var method in methods)
{
    Console.WriteLine($"方法: {method.Name}, 返回型別: {method.ReturnType.Name}");
}
```

## 元數據的應用場景

### 1. 框架支持

元數據使許多框架功能成為可能：

```csharp
// Entity Framework 中使用元數據描述資料庫結構
public class Product
{
    [Key]
    public int Id { get; set; }

    [Required, MaxLength(100)]
    public string Name { get; set; }

    [Column("product_price")]
    public decimal Price { get; set; }
}

// ASP.NET MVC 中使用元數據控制路由
[Route("api/[controller]")]
public class ProductsController : ControllerBase
{
    [HttpGet("{id}")]
    public IActionResult GetProduct(int id) { /* ... */ }

    [HttpPost, Authorize]
    public IActionResult CreateProduct(Product product) { /* ... */ }
}
```

### 2. 反射與動態程式設計

元數據支持反射和動態程式設計，允許在運行時探索和操作型別：

```csharp
// 透過反射動態創建物件並呼叫方法
Type type = Type.GetType("Namespace.Customer");
object instance = Activator.CreateInstance(type);
MethodInfo method = type.GetMethod("CalculateDiscount");
object result = method.Invoke(instance, new object[] { 100.0m });
```

### 3. 依賴注入與 IoC 容器

元數據使依賴注入和 IoC 容器能夠識別並解析依賴關係：

```csharp
// 在註冊服務時使用元數據
services.AddScoped<ICustomerService, CustomerService>();

// 使用屬性標記注入點
public class OrderController
{
    [Inject]
    public ICustomerService CustomerService { get; set; }
}
```

### 4. 序列化與反序列化

元數據指導序列化過程，確定哪些成員應被包含或排除：

```csharp
public class User
{
    public string Username { get; set; }

    [JsonIgnore]
    public string Password { get; set; }

    [XmlElement("EmailAddress")]
    public string Email { get; set; }
}
```

## 自定義元數據

開發者可以創建自定義元數據來支持特定的應用需求：

```csharp
// 自定義屬性以支持權限控制
[AttributeUsage(AttributeTargets.Method)]
public class RequirePermissionAttribute : Attribute
{
    public string PermissionName { get; }

    public RequirePermissionAttribute(string permissionName)
    {
        PermissionName = permissionName;
    }
}

// 使用自定義元數據
public class AdminController
{
    [RequirePermission("ManageUsers")]
    public IActionResult ManageUsers() { /* ... */ }

    [RequirePermission("ViewReports")]
    public IActionResult ViewReports() { /* ... */ }
}

// 在中間件中使用反射讀取元數據實現權限檢查
public class PermissionMiddleware
{
    public async Task Invoke(HttpContext context)
    {
        // 獲取當前請求對應的控制器和方法
        var endpoint = context.GetEndpoint();
        var methodInfo = endpoint?.Metadata.GetMetadata<ControllerActionDescriptor>()?.MethodInfo;

        if (methodInfo != null)
        {
            // 檢查方法是否具有 RequirePermission 屬性
            var permAttr = methodInfo.GetCustomAttribute<RequirePermissionAttribute>();
            if (permAttr != null)
            {
                // 檢查用戶是否擁有所需權限
                bool hasPermission = CheckUserPermission(context.User, permAttr.PermissionName);
                if (!hasPermission)
                {
                    context.Response.StatusCode = 403; // 拒絕訪問
                    return;
                }
            }
        }

        await _next(context);
    }
}
```

## 元數據與效能考量

雖然元數據和反射非常強大，但過度使用可能導致效能問題：

1. **反射操作較慢**：反射呼叫比直接方法呼叫慢
2. **緩存策略**：在頻繁使用反射時，應考慮緩存反射結果
3. **表達式樹**：對於頻繁執行的反射操作，考慮使用表達式樹編譯為委派
4. **程式集掃描**：避免重複掃描程式集，尤其在應用啟動時

```csharp
// 緩存反射結果以提高效能
private static readonly ConcurrentDictionary<Type, PropertyInfo[]> _propertyCache
    = new ConcurrentDictionary<Type, PropertyInfo[]>();

public PropertyInfo[] GetTypeProperties(Type type)
{
    return _propertyCache.GetOrAdd(type, t => t.GetProperties());
}

// 使用表達式樹優化反射
public static Func<object, object> CreateGetter(PropertyInfo property)
{
    var instance = Expression.Parameter(typeof(object), "instance");
    var convertInstance = Expression.Convert(instance, property.DeclaringType);
    var propertyAccess = Expression.Property(convertInstance, property);
    var convertResult = Expression.Convert(propertyAccess, typeof(object));

    return Expression.Lambda<Func<object, object>>(convertResult, instance).Compile();
}
```

## 結論

元數據是 .NET 平台的核心特性之一，它為許多進階功能提供了基礎支持。透過元數據，C# 程式擁有了自我描述和自我檢查的能力，使得框架設計、依賴注入、動態載入、代碼生成等技術成為可能。理解和善用元數據機制，是掌握 C# 進階程式設計的重要一環。
