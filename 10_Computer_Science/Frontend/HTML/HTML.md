#HTML 
HTML(HyperText Markup Language，[[超文本]][[標記 (Markup)]]語言) 是打造網頁的基本元素之一(網頁內容)
- HTML表述並定義網頁內容
- HTML使用「標記」(markup)來詮釋文字、圖像、或其他瀏覽器顯示的內容
- HTML(骨架)、CSS(衣服）、JS(動作)

---

HTML標籤語法元素：
1.  起始標籤(Opening tag): 功能為指出元素從何**開始**，並將元素名字夾在一對<> (Brackets)之間。  
2. 結束標籤(Closing tag): 功能為指出元素從何**結束**。起始標籤差在於名字前加一條斜線。
3. 內容(Content): 元素的內容
4. 元素(Element)：1 + 2 + 3

![[Pasted image 20230806202253.png]]

HTML標籤為採取[[物件導向 (Object-oriented)]]的概念

---
HTML Skeleton：建構HTML的基本標籤，目的在於告訴瀏覽器目前正在讀取什麼類型的文件，若無Skeleton則無法正確在瀏覽器上呈現HTML文件。 
> HTML網頁都由「head」以及「body」組成

Head: 和網頁資訊有關內容 (e.g. 作者、網頁語言、title tag)
- Meta標籤屬於self closing tag
- Base標籤可一次性設定所有Body中的a標籤(屬於self closing tag)

Body: 使用者可見內容 (文檔正文)。 (e.g. 標題、段落、圖像、超連結、表格、列表＿[[常用HTML Body標籤]])

---
元素類型(Block v.s. Inline Elements)
1. [[Block element]]
2. [[Inline element]]
---
表格(Table)製作：
四個常使用之標籤：
1. table：定義整個表格
2. tr (Table row)：建構每一行（橫排）
3. th (Table heading)：定義表格的標題單元格
4. td (Table data)：定義實際數據
此外，colspan(Column span)屬性：定義表格單元格應跨越的列數（垂直）
rowspan：定義表格單元格跨越的行數 （水平）
選擇性使用標籤：
- thead (Table head)
- tbody (Table body)
- tfoot (Table foot)

[[CSS表格設定]]
	 
---
表單(Form)製作
表單：可讓使用者填寫內容
- form標籤的action屬性定義了HTML文檔提交表單時，會將數據送至何處

規則：
1. form標籤的所有內容，**有設定name屬性才會被送到後端伺服器**
2. 常見的input標籤type屬性有：checkbox、email、file、number、password、radio(多選一，無法一次選擇多個選項，其藉由name標籤group選項)、range。
([ The Input (Form Input) element - HTML: HyperText Markup Language | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input))
> Number例子：
> <  input id="年齡" type="number" name="age" min="0" max="125" step="0.01" />
> 可設定step(單位調整數值)、max以及min數值

 
   >    Range舉例：
>. < input type = "range" /> 網頁會顯示拖拉橫桿



3. Method屬性：告訴瀏覽器如何將表單數據送至服務器
- GET：傳送**非隱密**資料，或向伺服器請求資料(Form data會被附加到action指定的URL，預設是用GET
 > < form action=""  method = "GET">
- POST：通常用於向伺服器寄送**隱密資料**時使用，或傳遞需儲存或處理資料
> < form action=""  method = "POST">

4. < button> 標籤若放在< form>標籤內，其預設type為「submit」
 - submit：提交表單(form)資料至伺服器
 - reset：重置所有數值(不建議使用)
 - button：無動作，可搭配JS提供click event
5. Select、Option標籤：可製造下拉式選單

![[Pasted image 20230809110048.png]]![[Pasted image 20230809110121.png]]![[Pasted image 20230809110121.png]]
![[Pasted image 20230809110250.png]]

6. Datalist：搭配option標籤，達到建議填入內容表格的目的

![[Pasted image 20230809111539.png]]
![[Pasted image 20230809111741.png]]

--- 
其他資訊：
1. HTML註釋語法
>  < !-- 註釋內容  -->

2. br標籤：用於需換行，但又不想要新的p標籤時。情境說明：同個p標籤內容不會換行，此時就可以使用br標籤
    hr(horizontal row)標籤：代表段落之間的主題中斷 
    
3.  若要新增不在鍵盤上的特殊符號，可使用HTML entity。使用方式：&開頭;(分號)結尾 (e.g @#169;  => Copyright符號)
4. index.html是伺服器在目錄中查找的默認文件 (i.e. 預設開啟的html文件)
5. self-closing tag(自閉合標籤)：代表void element，不能有任何content。
6. Favicon(Favorite icon)：瀏覽器可以將Favicon顯示於網址列中，也可置於書籤列表的網站名前。一般來說，icon的檔案名稱會設定為「favicon.ico 」
	> < link rel= "icon" href="./favicon.ico"> (需設在head標籤內)

---
HTML semantic tags：semantic(語意)是指一段code的含義(情境：過多的div標籤會無法直觀得知個部分功能為何，此時使用semantic tag可快速了解code)
舉例：< nav>、< header>、< section>、< footer>、< main>

![[Screenshot 2023-08-11 at 4.30.29 PM.png]]

---
[[HTML Bookmark]]