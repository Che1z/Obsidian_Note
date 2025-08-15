屬於三種節點的其中一種。

在DOM Tree中，每個HTML element(可能)有自己獨特的properties和methods。
當然除此之外，也有所有HTML elements都共同的properties和methods：

- addEventListener(event, callbackFn)
- appendChild(element)：和createElement()搭配
- childNodes
- children
每個節點都有childNodes屬性，return type為[[NodeList]]，內部包含此節點在DOM Tree之下的**第一層**的所有節點。

每個節點都有children屬性，return type為[[HTMLCollection]]，內部包含此節點在DOM Tree之下的**第一層**的所有節點。

不論使用childNodes還是children屬性，所獲得的DOM Tree元素集合，都只會是本身元素在DOM Tree下一層的元素。
如果希望獲得下下一層的元素，需要使用，像是element.children[i].children的語法，才能夠取得元素。
若是下下下一層的元素，就需要使用element.children[i].children[j].children的語法。

- parentElement
- classList (此物件可用的method有add(), remove(), toggle(), contains())

- getAttribute(attributeName)
- innerHTML ： innerHTML所填入的內容會被視為『HTML』程式碼
- innerText：innerText所填入的內容會被視為『純文字』
- querySelector(selector)
- querySelectorAll(selector)
- remove()
- style：可用來改變element object的inline styling，JS中的CSS屬性都是使用camelCase