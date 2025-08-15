Logical operator運算元是兩個任意資料型態，且運算結果為Boolean。
1. 當兩個運算子都是Boolean時：＆＆為且(And)、||為或(Or)
![[Pasted image 20230819230005.png]]
>  console.log (30 || 6) => 結果為30
2.  其餘運算子時(Short circuit)：
	> console.log (3 && 0) => 結果為0
	1. ＆＆： 若左側數值是Truthy，則返回右側值、若左側為Falsy value，則直接返回該值。
	> console.log (NaN || 30) => 結果為30
	2. ｜｜：若左側可以被轉為Truthy value，則返回左側值，反之返回右側值

	