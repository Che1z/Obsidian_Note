每個JS Object都有其properties以及method。Object的function就被稱為method。
- 屬性與對應值是一種key-value pair
- 獲取物件屬性的方式可透過dot notation or [ ]。
- JS object是一種hashtable。
- 在method中的[[this keyword]]指的是調用該方法的物件。若某個function沒有調用該function的物件，則[[this keyword]]指向window物件。
- JS當中function、array都是物件(Object)。Array以及function屬於special type of objects！
	- 若使用typeof去看 function會得出function (屬於bug)、而array則會得到object
		- 要如何check data是否為array? 使用isArray() method

---
[[Math object]]

