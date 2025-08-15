JS是如何「記憶變數」的？

需知：
- 變數並非直接保存數值，而是指向保存值的記憶體 
- Object、array等本質一樣是copy by value
- JS Engine由Call stack（函示執行處）以及Heap（儲存物件於記憶體的地方）組成
- 所有[[non primitive data type]]的資料儲存在Heap，反之所有[[copy by reference or value]]資料直接儲存在Call stack
- Address的Value不可再被改變！

下圖為舉例：
![[Pasted image 20230821114025.png]]

Primitive傳值解析：
  1. 建立一個 identifier （名稱就是宣告的變數名稱 e.g. age)
  2. 在Call stack建立一個記憶體(0001)
  3. 0001保存著數值30
  4. 宣告oldAge = age; (oldAge也指向0001)
  5. 宣告age = 31 (不能直接更改0001的數值至31)，因此新增記憶體0002，其保存數值就是新宣告的31

Reference傳值解析：
  1. 新增的me變數，其數值儲存在Heap裡，而Memory Address為D30F
  2. me identifier不會直接指向Heap (D30F)，而是指向在Call stack中的新記憶體(0003)，0003儲存指向Heap數據的參考位置(D30F），最終再藉其指向Heap的memory address (D30F )
  3. friend identifier同樣指向Call stack到0003再指向Heap的D30F
  4. friend.age = 27;時，會直接更改Heap裡頭的age至27 (因此me以及friend最終讀取到的值都是27)
  Note: 為何friend變數是以const宣告，卻還能更改數值？ 

const限制的是變數本身的重新賦值，而不限制你修改該變數所指向的內容（Heap 中的數據），而實際上friend數值未改變，一樣都是D30F，我們是透過更改Heap中的數據，更改最終讀取值。
