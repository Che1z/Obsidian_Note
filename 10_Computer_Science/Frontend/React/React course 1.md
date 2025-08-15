#前端 #JSX #React
- JSX最外層只能有一個根元素：一個元件並不能返回多個元素(就像一個函數不能返回多個值一樣)
> 錯誤範例：const element = < h2> Hello! < /h2> < h2> 你好 < /h2>
> 此範例內有『2個』h2標籤

>正確範例：const element = < div>< h2> Hello! < /h2> < h2> 你好 < /h2>< /div>
> 此範例內雖有『2個』h2標籤，但整體只輸出『１個』div

---
- JSX中的class：JSX可加入class來指定樣式，但屬性名稱需要改為『className』
> 舉例：const element = < div className="card">< h2> Hello！< /h2>< h2> 你好！< /h2>< /div>
---
- JSX中的屬性代入：在JSX中需要被視為JavaScript處理的部分，都需要使用大括號{}包住
> 舉例：const imgUrl = "https://i.pravatar.cc/150?img=38"; 
> < img src={imgUrl} />
--- 
- JSX 中的 style：在 JSX 中使用 style 設定樣式時，需在大括號內使用物件的方式設定，而物件內的樣式屬性則需使用駝峰命名法（camelCase）撰寫。
> const element = < div style={ {
>  backgroundColor: 'black', 
>  color: 'white' 
>     }
>   }> 
>   < h2> Hello！< /h2>< h2> 你好！< /h2> 
>   < /div>
---
- JSX中的for：在JSX中使用for屬性時，需注意將屬性名稱改為『htmlFor』。
> 舉例：
> < label htmlFor="firstName">名字：< /label>
>  < input id="firstName" type="text"/>

---
- 使用map方法將Array資料呈現在畫面上。需注意以下幾點：
1. 每筆資料都需要加上『key』值(不重複的字串與數字，辨認用)，通常會使用Array的資料內容，如：每筆資料的id。
    React會透過key分辨每筆資料的新增、刪除、排序。
    
舉例：在大括號 {} 中，使用 map() 將產品陣列資料用 < li> 列出。
> const listItems = (< ul>{ products.map(product => 
> < li key={product.id}> 
> {product.title} 
> < /li>) 
> }< /ul> 
> );

--- 
React Hook：[[Hook]]

---
- JSX的事件綁定：在JSX中，事件綁定是以小駝峰方式命名(camelCase)，因此onclick事件需改成onClick、onchangey則需改成onChange
> < button onClick={() => {}}> 按鈕 < /button>

---
React工作坊
[[React course1＿開發環境與JSX]] [[React course2]]