#WEB #前端 #HTML 

CSS(Cascading Style Sheet)階層式樣式表：用來設定網頁的樣式及佈局 
使用情境：改變字體、顏色、尺寸以及擺放內容位置或是動畫添加效果

---
CSS程式碼放置位置
1. inline styling：與HTML放在同一行
> < h1 style="color:red">國立故宮博物院 < /h1> 
> <h1 style="color:red">國立故宮博物院</h1>

2. internal styling：HTML文件和CSS文件放在一起。在head標籤裡面增加style標籤一次性定義所有標籤(e.g. h1、h2)

3. external styling：HTML文件和CSS文件分開(個為一份文件)，多份HTML可連接同一份CSS文件(常用檔名：style.css)。
如何連結？在head標籤中新增link標籤設定rel=“stylesheet" href="(檔案位置)"。
Note. rel = relationship

優缺點彙整：
inline styling：優先層級最高，有衝突時會以inline styling設定為主。缺點較為麻煩，較多標籤時不適合使用。
internal styling：撰寫方便，但無法同時應用於多個HTML文件
**external styling：最常見的放置位置，較容易維護。**

---
DOM(Document Object Model) Tree：

HTML的每一個標籤就是一個Node(節點)。瀏覽器加載網頁時，會建立該頁面的DOM Tree

![[Pasted image 20230809171254.png]]

---
常見CSS顏色選擇方式：
1. Color Keywords：CSS已設定保留的關鍵字 (e.g. red、black、silver、navy)
2. RGB：三個顏色分別使用256(2^8)組成 (e.g. 若為0, 0, 0則為黑色)。每個顏色為color channel，使用[[1 byte]]來儲存。
3. RGBA：同RGB，多使用alpha(透明度) channel，透明度範圍為0~1。
4. HEX：使用十六進制的數字來代表顏色。範圍為0, 1, 2, 3...9, A, B, C, D...., F。
5. HSL(Hue Saturation Lightness)：透過調整Hue(色相)、Brightness(亮度)、Saturation(飽和度)形成顏色，較少使用
---
CSS Selector選擇器：選擇哪些HTML標籤要套用樣式
- Universal Selector：可匹配任何類型的HTML element(語法：* )
- Element Selector：可選擇「特定的」HTML element(tag)
- ID Selector：可選擇「特定ID屬性」的HTML element(tag)。
 > CSS與HTML ID屬性配對，CSS語法需加 (#)
- Class Selector：可選擇「特定class屬性」的HTML element(tag)
> CSS與HTML Class屬性配對，CSS語法需加(.)

Class和ID差異在於：ID都需為獨一無二，Class則無需
Class和element selector可一起使用：選取特定element以及class的標籤

![[Screenshot 2023-08-10 at 1.40.01 PM.png]]
- Grouping Selector：一次性選擇數個HTML元素，並以逗號分隔
 > h1, h2, h3, h4, h5, h6 {color: red};
- Descendant(後裔) Selector：由兩個或多個用空格分隔的選擇器所組成 
- Attribute Selector：選擇所有具備相同元素 
> e.g.  input[type= "text"]{color:red}

特殊選擇器
- pseudo-class：用於指定所選元素的「特殊狀態」。例如，:hover(用戶滑鼠懸停在按鈕時改變樣式)、:nth-child() 可用於選擇第n個元素
> e.g.  input[type= "text"]：hover{color:red}

- pseudo-element：添加到選擇器的關鍵字，可設置「所選元素」的特定部分樣式。目的在於創造一個DOM Tree中不存在的HTML元素。
- 下方舉例為每個段落開始前添加">>"且其顏色為紅色
> p::before{
>   content: ">>" 
>   color: red
> }

---
CSS重點概念：
Inheritance(繼承)：
- Parents & Children
- Inherited & Non-Inherited properties：CSS中的某些元素會被子元素繼承，而某些則不會。
  會繼承的：color、font-family、font-size、font-weight、list-style-type、text-align  然而，[[user agent styling]]的優先度會高於inheritance，因此需要注意瀏覽器的預設樣式可能會覆蓋繼承屬性．

Conflicting Styling：由於一個HTML可連結數個CSS Stylesheet，且單一Stylesheet內部可能也出現重複設定的樣式，因此才有衝突的存在可能
- 處理原則：Priority(優先度), Specificity(特定度)以及Order rule(順序規則...上面會被下方程式碼覆蓋)
- Priority順序為：
1. Inline styling
2. User Stylesheet(內部由Specificity決定)
3. User Agent Stylesheet
4. Inheritance
- Specificity：選擇id會比class更specific
1. id - specificity(1, 0, 0)
2. class - specificity (0, 1, 0)
3. tag - specificity (0, 0, 1)
- Order rule：
1. 當有相同specificity選擇器時，後寫的選擇器樣式會被前寫覆蓋
2. 放在後方的< link> stylesheet會覆寫前方的< link> stylesheet
---
文字樣式text styling：
- font size ：設定字體大小，絕對單位 or 相對單位。[[CSS單位]]
- text-align：設置block element或table cell中的水平對齊位置 (Inline element無法使用)
- text-decoration：設置文本上裝飾線外觀(e.g. a標籤預設會有underline性質、line-through刪除線效果)
- line-height：設置文字行距
- line-spacing：設置文字水平間距
- font-family：為選擇元素指定一個或多個字體系列的優先列表 (內建會給三個字體，以防缺少字體)。 推薦工具： **Google font**
- text-indent：該段落內縮長度 (長度使用，如rem、em等長度單位)
- font-weight：設定文字粗度，數字越大越粗
---
背景樣式：圖片、圖片
- background-color：用來設定HTML元素背景顏色，值可以是顏色 or 特定關鍵字(e.g. transparent)
- background-image：元素上設定背景圖片，語法： url("路徑")
- background-size：設置元素背景圖像大小。
	1. 若值為contain，則會在容器內盡可能地等比例縮放圖像(不裁剪或拉伸圖像)。
	2. 當「容器大於圖像」時，會發生重複平鋪，此時要將background-repeat屬性設置為no-repeat才能避免發生。
	3. 當值為cover時，圖像會縮放至盡可能小的尺寸以填充容器(i.e. 高度和寬度完全覆蓋容器)，不留空白，倘若背景大於容器，多出的部分會被剪裁．
- background-position：設置背景圖像的初始位置。center：圖像居中，也可設置top、left、bottom、right。
- background：設定背景的shorthand(快速)方式，可一次設定所有背景樣式屬性，如：顏色、圖像、原點、大小或重複方法。(e.g. background:green 背景顏色：綠、background: url("test.jpg")：設置圖片)

---
Box Model （重點！)

在CSS中，每一個block element都可視為一個box，且該box由margin, border, padding以及content所組成。inline element僅使用Box model中定義的一部分屬性。

- content：顯示內容的區域，可使用width和height調整區域大小
- padding：位於content周圍的區域，在content和border之間．可使用padding屬性調整大小
- border：包住content與padding的邊框，可使用border屬性調整大小
- margin：border外的區域，可使用margin屬性調整大小
padding、border以及margin都可再分別設定上下左右屬性．border可特別設定border-radius屬性(外框圓滑度) 


- width屬性：為元素的寬度，預設情況下，該屬性定義內容為content寬度。Block element預設寬度為100%。若box-sizing設置為border-box，則會被設定為border區域的寬度。
- height屬性：為元素的高度，預設情況下，該屬性定義內容為content寬度。若box-sizing設置為border-box，則會被設定為border區域的高度。
	1. Block element的高度取決於content(高度為Auto計算)，因此若直接設定height為50%會無法正常顯示，除非設定body、html(父元素)高度為100% or 100px....(定義父元素高度，讓子元素有參考值計算)。
	2. 大多數情況，不會設定元素高度，若有設定需考量overflow(元素超出容器)的情況，此時可設定overflow屬性來選擇處理方式：
		- visible：content不會被修剪，可以呈現在元素框之外
		- hidden：如需要，內容會被剪裁以適合元素(容器)，不提供滾動條。
		- scroll：如必要，內容需被剪裁以適合填充框，瀏覽器顯示移動軸。
		- 若要設定指定方向的overflow屬性：可選擇overflow-x或overflow-y

Box-sizing：CSS預設屬性為content-box，意指設定width、height為content寬高度。
若設定為border-box，則設定的width、height會包含content、padding以及border(不含margin)。

---
Display屬性：每個HTML元素都有兩種display類型
1. outer display type：有三種可設定值，可決定box在網頁的排版位置
	1. Block：預設寬度為100% (佔據一整行)
	2. Inline：並排直到超出視窗範圍再換行 (a標籤display預設為inline)
	3. inline-block：除空間足夠時不會換行外其餘都和block一樣

![[Pasted image 20230811104039.png]]
![[Screenshot 2023-08-11 at 10.58.29 AM.png]]
2. inner display type
	1. [[flex]]
	2. grid

---
Position：設置HTML元素在文檔的定位方式。top、right、bottom和left屬性確定定位元素最終位置，可設定的值包含：
1. static：元素根據文檔的[[normal flow]]進行定位。top、right、bottom、left和[[z-index]]屬性設定會無效。Static並不是[[positioned element]]
2. relative：HTML element根據[[normal flow]]定位，然後根據top、right、bottom和left進行偏移
3. absolute：該元素會從[[normal flow]]中移除，不保留任何空間。根據top、right、bottom和left的值相對於自身進行定位，定位對象則參考[[closest positioned ancestor]]，若找不到則會不斷地往上找，倘若最終都沒有，參考對象會是initial containing block(瀏覽器初始視窗)
4.  fixed：該元素會從[[normal flow]]移除，不保留任何空間．根據top、right、bottom和left的值相對於自身進行定位，固定在瀏覽器視窗的固定位置。參考對象是initial containing block(瀏覽器初始視窗)
5. sticky：是relative position和fixed position的混合體。HTML element被視為相對定位，直到它超過指定的threshold(臨界點)，此時才會被視為固定定位。舉例：.one { position: sticky ; top: 10px}，此時class one的元素保持relative position，直到元素與瀏覽器最上方的空間小於10px。可用於固定導覽列(nav)時使用，並搭配box shawdow優化網頁瀏覽體驗。
--- 
Stacking Context (用堆疊環境去理解)：HTML元素沿著z軸的3D概念，Stacking context形成情況包含以下幾點 (並非全部列出)
1. Root element of the document (< html>)
2. 任何有position設定為absolute或relative的元素，且z-index的值不是Auto，則內部形成新的stacking context
3. 任何有設定position為fixed或sticky的元素

---
Transition設定：可幫助設定某個CSS屬性轉換時的timing function以及速度，本身是一個shorthand property， 可一次性設定transition-property、transition-duration、transition-timing以及transition-delay。

> 常見transition設定：
> (CSS) property name｜duration｜easing (Timing) function (可有可無)[緩動函數 (Easing function))](https://easings.net/zh-tw)

Transform屬性：旋轉、縮放、傾斜或平移HTML元素。可設定值：translate(移動)、rotate、scale，每個值又可再分別設定x、y、z方向的變換。
> {transform : translate(-50%, -50%)} ...水平置中
> {transform : rotate(45deg)} 、 {transform : rotateX(45deg)} ...旋轉

---
CSS動畫：可藉由transition以及transform屬性合併來完成，然而若要製作更複雜的動畫，則可透過CSS animation屬性完成客製化。
每個動畫可設定：
1. animation-name (keyframes)
2. animation-duration：動畫進行多久
3. animation-timing-function：等同於transition timing function
4. animation-delay：動畫前等多久
5. animation-iteration-count：循環幾次
6. 以及animation-direction, animation-fill-mode, animation-play-state等屬性
animation屬性是shorthand property，可一次性設 定上述多個相關屬性
---
[[響應式網頁設計(RWD)]]

---
[[免費圖片、圖案網頁]]

---
[[Sass]]