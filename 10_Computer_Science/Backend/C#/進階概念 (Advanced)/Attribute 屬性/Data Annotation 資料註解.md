# C# Data Annotation（資料註解）

Data Annotation 是一種特殊用途的 [[Attribute 屬性]]，主要用於資料驗證和描述，位於 `System.ComponentModel.DataAnnotations` 命名空間下。

## Data Annotation 的基本概念

Data Annotation 為資料模型提供宣告式驗證和元數據標記，廣泛應用於 ASP.NET MVC、Entity Framework 等框架。

```csharp
public class Product
{
    [Required]
    public string Name { get; set; }

    [Range(0.01, 10000.00)]
    public decimal Price { get; set; }
}
```

## 常用的 Data Annotation

### 驗證註解

```csharp
public class User
{
    [Required(ErrorMessage = "用戶名為必填項")]
    public string Username { get; set; }

    [EmailAddress]
    [Required]
    public string Email { get; set; }

    [Phone]
    public string PhoneNumber { get; set; }

    [Range(18, 120, ErrorMessage = "年齡必須在18到120歲之間")]
    public int Age { get; set; }

    [StringLength(100, MinimumLength = 8)]
    [DataType(DataType.Password)]
    public string Password { get; set; }

    [Compare("Password", ErrorMessage = "密碼和確認密碼不一致")]
    public string ConfirmPassword { get; set; }

    [Url]
    public string Website { get; set; }

    [RegularExpression(@"^[A-Z]{2}\d{6}$", ErrorMessage = "ID格式不正確")]
    public string EmployeeId { get; set; }
}
```

### 顯示註解

```csharp
public class Product
{
    [Display(Name = "產品名稱")]
    public string Name { get; set; }

    [Display(Name = "產品說明")]
    [DataType(DataType.MultilineText)]
    public string Description { get; set; }

    [Display(Name = "價格")]
    [DisplayFormat(DataFormatString = "{0:C2}")]
    public decimal Price { get; set; }

    [Display(Name = "發布日期")]
    [DisplayFormat(DataFormatString = "{0:yyyy-MM-dd}", ApplyFormatInEditMode = true)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; set; }

    [ScaffoldColumn(false)] // 在脚手架生成時忽略
    public Guid InternalId { get; set; }
}
```

### 資料庫相關註解

```csharp
public class BlogPost
{
    [Key] // 主鍵
    public int Id { get; set; }

    [Required]
    [MaxLength(100)]
    [Column("Title")] // 指定資料庫欄位名稱
    public string Title { get; set; }

    [MaxLength(500)]
    public string Summary { get; set; }

    [Required]
    [Column(TypeName = "ntext")] // 指定資料庫欄位類型
    public string Content { get; set; }

    [ForeignKey("Author")] // 外鍵
    public int AuthorId { get; set; }

    public virtual User Author { get; set; }

    [Timestamp] // 樂觀並發控制
    public byte[] RowVersion { get; set; }
}
```

## 手動驗證 Data Annotation

```csharp
public bool ValidateModel(object model)
{
    var validationContext = new ValidationContext(model);
    var validationResults = new List<ValidationResult>();
    bool isValid = Validator.TryValidateObject(model, validationContext, validationResults, true);

    if (!isValid)
    {
        foreach (var error in validationResults)
        {
            Console.WriteLine(error.ErrorMessage);
        }
    }

    return isValid;
}
```

## Data Annotation 的應用場景

- Web 表單驗證
- ORM 模型定義
- API 參數驗證
- UI 自動生成（如 Scaffolding）
- 資料庫結構生成
- 動態資料顯示格式化

Data Annotation 使驗證邏輯直接附加於模型上，實現了驗證邏輯與業務邏輯的分離，提高了代碼的可維護性和清晰度。
