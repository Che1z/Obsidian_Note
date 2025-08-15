# MetadataType in MVC 🎭


1. 主要目的 🎯
    - 允許在不直接修改自動生成的 model 類的情況下，添加或修改元數據。
    - 這種方法特別適用於使用 Database First 或 Model First 方法生成的 model。
2. 保護自動生成的代碼 🛡️
    - 自動生成的 model 類通常不應該被直接修改，因為:
    - a) 這些修改可能在數據庫結構變更時被覆蓋 
    - b) 直接修改可能導致版本控制問題
1. 分離關注點 👥
    - Model 類保持純粹的數據結構
    - 元數據（如驗證規則、顯示名稱等）被移到單獨的類中
2. 靈活性 🌈
    - 可以輕鬆地更改顯示名稱、添加驗證規則等，而不影響原始 model
    - 便於實現多語言支持和本地化
3. 實際應用 🔧
    - 你可以為自動生成的 model 添加驗證規則
    - 更改屬性在表單和視圖中的顯示方式
    - 添加自定義錯誤消息

## 使用方法 🔧

```c#
// 自動生成的 model（不變）
public partial class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}

// 元數據類（可以自由修改）
public class UserMetadata
{
    [Required(ErrorMessage = "姓名為必填項")]
    [Display(Name = "姓名")]
    public string Name { get; set; }

    [EmailAddress(ErrorMessage = "請輸入有效的電子郵件地址")]
    [Display(Name = "電子郵件")]
    public string Email { get; set; }
}

// 將元數據類與原 model 關聯
[MetadataType(typeof(UserMetadata))]
public partial class User
{
    // 無需添加任何內容
}
```



## 應用場景 🌈

`假設我們有一個自動生成的 User model,想要在不修改原始類的情況下,更改屬性在View中顯示的名稱,特別是將英文名稱改為中文。`

1. 原始 Model 類 (自動生成) 🔒
 ``` c#
public partial class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
    public DateTime DateOfBirth { get; set; }
}
```
2. 創建 MetadataType 類 🆕

```c#
public class UserMetadata
{
    [Display(Name = "姓名")]
    public string Name { get; set; }

    [Display(Name = "電子郵件")]
    public string Email { get; set; }

    [Display(Name = "出生日期")]
    public DateTime DateOfBirth { get; set; }
}
```

3. 關聯 MetadataType 與原始類 🔗
```c#
[MetadataType(typeof(UserMetadata))]
public partial class User
{
    // 無需添加任何內容
}
```

4. 效果展示 🌈

a. 在視圖中使用 HTML Helper:
```html
 @Html.LabelFor(model => model.Name)
```
這將顯示 "姓名" 而不是 "Name"

b. 在表單中:
```html
<div class="form-group">
    @Html.LabelFor(m => m.Name, new { @class = "control-label" })
    @Html.EditorFor(m => m.Name, new { @class = "form-control" })
</div>
<div class="form-group">
    @Html.LabelFor(m => m.Email, new { @class = "control-label" })
    @Html.EditorFor(m => m.Email, new { @class = "form-control" })
</div>
<div class="form-group">
    @Html.LabelFor(m => m.DateOfBirth, new { @class = "control-label" })
    @Html.EditorFor(m => m.DateOfBirth, new { @class = "form-control" })
</div>
```

這將顯示中文的標籤名稱。 

c. 在 scaffolding 生成的視圖中: 如果使用 Visual Studio 的 scaffolding 功能生成 CRUD 視圖,它會自動使用這些自定義的顯示名稱。

## 優點 🌟

- 原始 Model 類保持不變,避免直接修改自動生成的代碼 🔒
- 集中管理所有顯示名稱,提高可維護性 🌍
- 提高代碼可維護性 📈
- 適用於自動生成的模型類 🤖

---

> [!TIP]  MetadataType 特別適合處理大型專案或需要多語言支持的場景。

---

## 注意事項 ⚠️

- 確保 MetadataType 類中的屬性名稱與原始 Model 類完全匹配
- 只有在 MetadataType 類中定義的屬性才會受到影響
- 這種方法不僅限於更改 Display Name,還可以添加其他數據注解,如驗證規則等