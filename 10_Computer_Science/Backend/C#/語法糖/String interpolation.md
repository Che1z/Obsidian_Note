# C# 字串內插 (String Interpolation)

字串內插（或稱字串插值）是 C# 6.0 引入的功能，透過在字串前加上 `$` 符號，可以直接在字串中嵌入變數或運算式。

```csharp
string name = "World";
int version = 12;

// 使用字串內插
string message = $"Hello, {name}! Welcome to version {version}.";
Console.WriteLine(message); // 輸出: Hello, World! Welcome to version 12.
```

---

### 為何這是語法糖？

字串內插是一種語法糖，它極大地簡化了字串的格式化。在編譯時，`$` 字串會被轉換成對 `string.Format()` 方法的呼叫。這讓程式碼比使用傳統的字串串接 (`+`) 或 `string.Format()` 更簡潔、更易讀，且不易出錯。

---

### 不使用語法糖的寫法

在 C# 6.0 之前，格式化字串主要有兩種方式：

**1. 使用 `string.Format()` (直接對應)**
這是字串內插在底層的實際運作方式。

```csharp
string name = "World";
int version = 12;

string message = string.Format("Hello, {0}! Welcome to version {1}.", name, version);
Console.WriteLine(message);
```

**2. 使用字串串接 (`+`)**
這種方式在處理多個變數時會變得很冗長且效率較差。

```csharp
string name = "World";
int version = 12;

string message = "Hello, " + name + "! Welcome to version " + version + ".";
Console.WriteLine(message);
```
