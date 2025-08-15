`GridView`是用來取代`DataGrid`
`GridView`會以`HTML`表格形式呈現，預設有選取、排序、編輯和分頁等功能（無預設『新增』功能）

有`ItemTemplate`和`EditItemTemplate`兩種形式

`GridView屬性`：
	`DataKeyName屬性`：代表資料的『主鍵(Primary Key)』
	`DataSourceID屬性`：只有使用『資料來源』控制項時才會用上

`Select功能和EnableSortingAndPagingCallbacks衝突`：
	兩者會有衝突是因為`EnableSortingAndPagingCallbacks`能實現回傳`GridView` 使用 AJAX 技術在`Callback`期間僅回傳必要的資料(`通常僅回傳當前頁面顯示的資料行`)，而`Select`需要回傳整體資料才可正常運行

StringFormat設定：
![[Pasted image 20240304100133.png]]



