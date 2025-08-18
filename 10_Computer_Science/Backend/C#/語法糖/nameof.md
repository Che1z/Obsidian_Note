# C# nameof 運算子

`nameof` 運算子是 C# 6.0 新增的功能，它會在編譯時期取得變數、型別或成員的名稱作為字串，而不需要在程式碼中硬編碼 (hardcode) 名稱。

```C#
public void ProcessOrder(int orderId)
{
    if (orderId <= 0)
    {
        // 使用 nameof 取得參數名稱
        throw new ArgumentNullException(nameof(orderId));
    }
}
```

---

### 為何這是語法糖？

`nameof` 是一種編譯時的語法糖。它的主要目的是避免在程式碼中使用「魔術字串」（Magic Strings），也就是直接寫死的字串。

使用 `nameof` 的好處是，如果您未來透過重構工具更改了變數或成員的名稱，`nameof` 的結果會自動更新。如果使用硬編碼字串，則必須手動尋找並修改所有相關的字串，否則會導致程式碼與實際情況不符，引發錯誤。

---

### 不使用語法糖的寫法

在沒有 `nameof` 之前，開發者只能手動輸入成員名稱的字串。

```C#
public void ProcessOrder(int orderId)
{
    if (orderId <= 0)
    {
        // 硬編碼字串 "orderId"
        throw new ArgumentNullException("orderId");
    }
}
```
這種寫法的缺點是，如果有一天參數 `orderId` 被改名為 `transactionId`，但字串沒有跟著修改，那麼拋出的例外訊息就會是錯誤的。
