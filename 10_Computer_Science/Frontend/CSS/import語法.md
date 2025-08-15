@import (匯入)

可將SCSS檔案彙整成一份CSS檔案

舉例：
```
_variable.scss檔案 (檔名使用_開頭代表為Local檔案，防止該scss檔案編譯成css檔案)
在all.scss中, 第一行輸入
@import "variable";
```  