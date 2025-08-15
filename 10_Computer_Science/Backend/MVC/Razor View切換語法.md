# Razor 視圖語法深度解析

## 1. 基礎語法元素

### @符號
- **用途**: 內嵌單行 C# 表達式
- **示例**: 
``` html
  <p>當前時間: @DateTime.Now</p>
```
### @{}代碼塊

- **用途**: 多行 C# 代碼執行
- **示例**
```html
@{
  var message = "Hello, World!";
  var currentTime = DateTime.Now;
}
```

## 2. HTML 與 C# 代碼混合技巧

### 文本輸出方法

1. `<text>` 標籤
```html
@if (isTrue) {
  <text>這是真的</text>
}
```
2. @:語法
``` html
@if (isTrue) {
  @: 這也是真的
}
```
### 循環中的混合使用 :
``` html
@for (int i = 1; i <= 5; i++)
{
    <div>
        項目 @i:  
        @if (i % 2 == 0)
        {
            @: 偶數
        }
        else
        {
            @: 奇數
        }
    </div>
}
```
### 循環中的混合使用:
``` html
@for (int i = 1; i <= 5; i++)
{
    <div>
        項目 @i: 
        @if (i % 2 == 0)
        {
            @: 偶數
        }
        else
        {
            @: 奇數
        }
    </div>
}
```