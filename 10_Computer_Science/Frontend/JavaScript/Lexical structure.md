代表基本語法，是一種語言的最基本語法，例如，變量名稱的外觀、註釋的分隔符以及如何將程式語句分開。以下為JS中的幾點Lexical structure：
1. Case sensitive：大小寫是有差別的
2. 空白鍵、換行鍵等，在JS會被忽略。因為在伺服器上JS程式碼都會被執行minification(刪除空白鍵、換行鍵)，藉此減少檔案大小。
3. 變數名稱需要由文字、underscore( _ )、dollar sign($)當開頭，不能使用『數字』
4. JS內部有保留字，例如：null, of, if, then, in, finally, for, while, break, continue, switch, try, let, const, var等，這些都不能當作變數名稱。
5. JS使用Unicode字元集合，因此String內部可由任何Unicode文字組成。
6. Semicolons( ; )可用來分隔程式語句。非必需使用