全名為Syntactically Awesome Stylesheets，是一種將CSS視為程式語言的網頁開發技術。Saas的特點在於支援設定變數、函數、[[import語法]]、nested語法等等，使得網頁開發者可以快速寫出高相容性、跨瀏覽器的CSS語法。

Sass的副檔名為scss，其無法直接被瀏覽器讀取(只能讀取HTML、CSS)，因此需透過編譯器(VS code擴充程式)將scss編譯成CSS文件後，才能被HTML文件使用套用樣式。

若scss文件有bug則無法成功編譯出css文件，每次更新scss文件後，都需要重新編譯出相對應的CSS文件

常見且主要功能包含：
1. Nested CSS (巢狀語法)
2. 變數設定(Udemy_2023全端網頁開發_Section 7_ 80. @15:00)：可設定變數，方便後續一次性更改設定 (前面需添加＄)
```
 $themecolor : red; //設定變數themecolor
 
 h1{
   color: $themecolor
}
```
 3. self ampersand (&)：透過&可選擇到父元素選擇器（ [[連接符＆]]）
4. import：語法：@import" ./ "，可匯入其它sass程式碼。方便於分類以及重複利用。匯入檔案名稱開頭必須要有底線（ _ ）
5. mixin：可視為儲存多行程式碼的變數 [[Mixin]]
6. function語法：和[[Mixin]]差別在於會產生值
```
@function divide($a, $b){
  @return $a / $b;
}

//用在nav上
nav{
  margin: divide(60/2)px;
}
```

[[SCSS]]

調色：[[調色(darken, lighten)]]