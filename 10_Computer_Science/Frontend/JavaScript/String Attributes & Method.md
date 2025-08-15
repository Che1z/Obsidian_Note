JS中的String有可用的Attributes以及Methods。常見的有：

屬性：
- length屬性 - return String的長度。
- [n]屬性- return index第n項的字。(index從0計算)
方法：
- slice(indexStart [, indexEnd])方法：提取字符串的一部分並將其作為新String返回，而不修改原始字符串。indexStart是inclusive(包含)，而indexEnd則是optional exclusive(不包含)。
- indexOf(substring) - return substring的index位置。若找不到substring，則會return -1。
- toUpperCase()、toLowerCase()：return轉換成大、小寫的String。此方法不影響String本身。
- split(pattern)：接受一個pattern並透過搜尋將字符串轉成有序的array，然後return該array。Pattern可以是regular expression
- startsWith(s)：確認string是否以指定字串(s)開頭，結果返回true或false。
- endsWith(s)：確認string是否以指定字串(s)結尾，結果返回true或false。
- includes(s)：確認string內部使否包含s，結果返回true或false。
- charCodeAt(n)：表示給定索引處n的UTF-16 code unit，結果返回一個介於0和65535之間的整數，