bit是最小資料單位，0或1，指的是在位元層面上智慧地操作的運算方式。
在decimal system中可用數字為(0~9)，而在binary system中可用數字只有(0、1)，如下圖所示：
![[Pasted image 20230819230808.png]]
且二進制與十進制之間能透過公式轉換(有固定關聯)

在JS中Bitwise operator會將數字operand視為32bits的數字，並對每個bit進行運算。
- a＆b：在兩個operand的對應位為1的位置，返回1，若否則返回0。
- a｜b：在兩個operand的對應位為0的位置，返回1，若有一個為1就返回1。
- a＾b：在兩個operand的對應位相同的位置返回0，若有不同的返回1。(XOR運算)
下列三點為CPU相關內容才會使用到：
- ~a：反轉operand的每個bit
- a<<b：將二進制表示中的a向左移動b位，最右邊的空位將填充為 0。。
- a>>b：將二進制表示中的a向右移動b位，丟棄任何被移除的bits。
---
何時會需要使用？
1. 使用編碼運算
2. 資料傳出，sockets programming, ports
3. 資料加密、SHA函數(後端)
4. 作業系統、CPU
5. Finite State Machine
6. Graphics，如影像處理、人工智能