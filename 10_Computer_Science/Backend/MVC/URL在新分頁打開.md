## 背景 📚

當使用 `[DataType(DataType.Url)]` 時,默認情況下生成的連結會在當前頁面打開。但有時我們希望在新分頁中打開這些連結。

## 解決方案 🛠️

### 1. 自定義 Display Template 🎨

1. 在 `Views/Shared/DisplayTemplates` 資料夾中創建 <mark style="background: #FFB86CA6;">Url.cshtml</mark> 文件：
```html
@model string
<a href="@Model" target="_blank">@Model</a>
```

2. 在你的 Model 中使用 DataType 屬性：
```c#
public class MyModel
{
    [DataType(DataType.Url)]
    public string Website { get; set; }
}
```
3. 在View中使用
```html
@Html.DisplayFor(m => m.Website)
```

## 2. 使用 HtmlHelper 擴展方法 🛠️

創建一個 HtmlHelper 擴展方法來生成帶有 `target="_blank"` 的 anchor 標籤。

1. 創建擴展方法：
```c#
public static class HtmlHelperExtensions
{
    public static IHtmlContent UrlWithNewTab(this IHtmlHelper htmlHelper, string url)
    {
        return new HtmlString($"<a href='{url}' target='_blank'>{url}</a>");
    }
}
```
2. 在 View 中使用：
```html
@Html.UrlWithNewTab(Model.Website)
```
