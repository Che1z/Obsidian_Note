起源：幫助記得ＣＳＳ語法，避免因回想而中斷思緒

用法：
1. 變數
```
// 建立mixin(變數概念)
@mixin blueSize{
  color: blue;
  font-size: 13px;
}

.header h1{
  backgorund: black;
  @include blueSize;
}
```

2. 變數參數
```
@mixin button-style($bg-color, $text-color){
  background-color: $bg-color;
  color: $text-color:
  padding: 10px;
}

// 引用mixin參數
.button { 
  @include button-styles(#3498db, #ffffff); 
}
```

3. [[content]]