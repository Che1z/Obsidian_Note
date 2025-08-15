在JS中，Window object代表目前程式碼正在運行的電腦視窗 (通常指瀏覽器視窗)

以下的window字詞在撰寫時可忽略

Window object常見的**methods**包含：
- window.alert()：在視窗顯示對話框
- window.addEventListener()：將事件監聽附加至Window object
- window.clearInterval()：將setInterval()所重複執行的程式暫停
- window.prompt()：return用戶在提示對話框中輸入的文字 (return type是string)
- window.setInterval()：每次經過給定的毫秒數時安排一個函數執行

在物件導向中，Object的**properties**也可以是一個Object。
Window object常見的properties包含：
- window.console：return一個console object。console object可以對瀏覽器的debugging console進行控制與訪問。常用methods為log(), error()。
- window.document：return window包含的文檔 (HTML文件)。
- window.localStorage：return一個local storage物件。
- window.sessionStorage：return一個session storage物件。

---
[[Document Object]]