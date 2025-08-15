JS數字格式允許我們表示介於(2^-253)和(2^253)之間的所有整數。若超出範圍則可能丟失數字的精度。
		數字支援的運算符號：加法、減法、乘法、除法、remainder operator(%)、exponentiation operator(* **)、++、--、+=、-=、/=、* ***=等等。

Number Method：JS是個[[物件導向 (Object-oriented)]]的程式語言，所以JS數字可被視為是Object。以下為常見Methods：
1. toString()： return一個數字的String
2. toFixed()：return被轉換後的數字，到小數點後第n位數。需注意：二進位無法精準表示所有小數，因此有可能導致意外結果，如0.1 + 0.2 === 0.3 結果會是return false。

---

NaN屬性：表示Not-A-Number的值，當使用String或其他資料類型進行數學計算時，若無法計
Infinity：任何正整數乘以Infinity都會是Infinity，除以Infinity的任何數都是0