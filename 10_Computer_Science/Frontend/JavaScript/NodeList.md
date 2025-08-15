本身不是Array而是Array-like object
其內容含三種節點：
1. HTML元素節點 ([[Element nodes]])
2. 文字節點 (Text node)：只有childNodes屬性，若使用children屬性，只會看到undefined
3. 註解節點 (Comment node)：只有childNodes屬性，若使用children屬性，只會看到undefined

屬於靜態(static)。

![[Pasted image 20230910145103.png]]