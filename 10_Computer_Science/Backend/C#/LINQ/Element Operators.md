`Element Operators`使用index或condition從序列中找尋單一元素。

	1. First / FirstOfDefault : 找尋第一個元素
	  First:兩種overload版本，First()會直接找第一個元素，First(predicate)則會找『符合條件』後的第一個元素。
	  FirstOfDefault : 若沒有找到第一個元素，回傳該序列類型的Default值 
	  
	2. Last / LastOfDefault : 與First / LastOfDefault邏輯相同
	   
	3. ElementAt / ElementAtOrDefault ：回傳特定位置的Element值
	   ElementAt : 若提供的index值不存在或超出範圍，則拋出ArgumentOutOfRange Exception
	   ElementAtOrDefault : 若index值不存在值或超出範圍，則回傳Default值
	   
	4. Single / SingleOrDefault：回傳單一數值，只是適用於單一數值序列
	 Single : 確保序列中只有一個元素，若沒有元素或有多個元素，則拋出異常
	 SingleOfDefault：確保序列中最多有一個元素，若沒有元素或有多個元素則拋出異常
	   
	5. DefaultIfEmpty：若序列不為空，回傳序列中的值;若序列為空，則回傳Default值