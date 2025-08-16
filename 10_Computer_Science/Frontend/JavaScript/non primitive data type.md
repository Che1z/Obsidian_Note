1. [[Object]]
2. [[JavaScript/Array]]
3. [[Function]]

賦值操作複製[[non primitive data type]]時會將變數從一個變數複製到另一個變數，兩者引用同一個物件，因此修改其中一個變數所指向的物件也會影響到另一個變數。

考量到object、array以及function數據量較大，因此設計時才會設計[[copy by reference or value]]
![[Pasted image 20230821114025.png]]

