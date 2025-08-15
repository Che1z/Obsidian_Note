兩種寫法：
1. Lambda expression
2. SQL like expression

最終執行時，都是以Lambda expression再轉成SQL語法

然而即使如此，兩者之間效能差異並不大，主要還是取決於最終轉成的T-SQL指令，決定最終效能