在JS中，Array並不是[[Primitive data type]]
Array使用時機：將用途或性質相近的數據儲存一起時

核心特質：
1. JS Array是可調整大小的，並可以包含不同資料類型的混合。
2. JS Array中的元素必須使用非負整數作為index來訪問。
3. JS Array的第一個元素在index 0處，最後一個元素在array.length - 1的位置。
4. JS Array複製時會複製reference。(意思是copy by reference，指向物體改變)

---
[[Array Attributes & Method]]