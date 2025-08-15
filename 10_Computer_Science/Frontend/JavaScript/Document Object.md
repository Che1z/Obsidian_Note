Document object為Window底下一層屬性。

常見Document object的methods有：
- window.document.addEventListener()
- window.document.createElement (tagName)：tagName舉例：h1、h2標籤...
- window.document.getElementById (id)：會return第一個id相符合的element object
-  window.document.getElementByClassName (className)：return一個動態(live)的[[HTMLCollection]](內部元素包含所有指定className的元素)。

現代主要透過querySelector (JS Method)來選取HTML元素，使用CSS查詢HTML元素。
- querySelector (selectors)：return 第一個符合特定選擇器群組的element object。採用深度優先搜尋演算法。
- querySelectorAll (selectors)：return一個靜態(not live) [[NodeList]]，表示與指定選擇器組匹配的元素列表。

![[Pasted image 20230910144753.png]]