兩大類別：
1. Absolute unit：有預設數值或現實生活定義的單位(px、cm、in、mm...)。px = 2.54cm，瀏覽器預設p標籤是16px
2. Relative unit：相對於某種數值的單位
	 1. em：相較於parent element的長度。再多層DOM Tree中，越下層的element其em值越難以計算。 (1em會相同於parent element、2em則為parent的兩倍大)
	 2. rem(root em)：rem會找到< html>元素的設定。瀏覽器預設其font size為16px，因此1em等於16px 
	 3. vw(viewport width)：是指目前viewport的寬度的0.01。100vw長度會略寬於網頁寬度，也因此會導致產生horizontal scrollbar。
	 4. vh(viewport height)：是指目前viewport高度的0.01
	 5. %：相較於parent element的百分比數值

> 建議使用rem(大小)、%(寬度)