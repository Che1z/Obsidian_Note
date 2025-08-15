# C# DataType 屬性初學者指南 🚀

## 什麼是 DataType 屬性? 🤔

當使用 `DataType` 屬性時，ASP.NET MVC 會生成適當的 HTML5 標籤，從而改變輸入字段的行為和顯示方式。
屬於 `System.ComponentModel.DataAnnotations` 命名空間。

## 常見的 DataType 屬性 📊

| 屬性                       | 描述     | HTML5 輸入類型     |     |
| ------------------------ | ------ | -------------- | --- |
| `DataType.Text`          | 普通文本   | `type="text"`  |     |
| `DataType.EmailAddress`  | 電子郵件地址 | `type="email"` |     |
| `DataType.Date`          | 日期     | `type="date"`  |     |
| `DataType.PhoneNumber`   | 電話號碼   | `type="tel"`   |     |
| `DataType.Url`           | URL    | `type="url"`   |     |
| `DataType.Currency`      | 貨幣值    | -              |     |
| `DataType.MultilineText` | 多行文本   | `<textarea>`   |     |
|                          |        |                |     |
| [[URL在新分頁打開]]            |        |                |     |

## 使用示例 💡

```c#
public class User
{
    [DataType(DataType.EmailAddress)]
    public string Email { get; set; }

    [DataType(DataType.Date)]
    public DateTime BirthDate { get; set; }
}

```

## 其他相關屬性 🛠️

- `[Display(Name = "Custom Name")]`: 自定義顯示名稱
- `[DisplayFormat(...)]`: 自定義顯示格式
- `[Required]`: 必填字段
- `[StringLength(100, MinimumLength = 10)]`: 字符串長度限制
- `[Range(1, 100)]`: 數值範圍限制

## 示例: 組合使用 🔗

```c#
public class Product
{
    [Required]
    [Display(Name = "產品名稱")]
    [StringLength(50, MinimumLength = 3)]
    public string Name { get; set; }

    [DataType(DataType.Currency)]
    [Range(0, 1000000)]
    [Display(Name = "價格")]
    public decimal Price { get; set; }
}
```

## 注意事項 ⚠️

1. `DataType` 主要影響顯示,不影響數據存儲
2. 某些 `DataType` 可能需要額外的客戶端驗證
3. 使用 `DataType` 可以提高用戶體驗和表單驗證效果