何謂useEffect？ 當狀態改變時，重新執行的特定函式
為何要使用？ 當useState 觸發時，全元件的資料都會更新一次。若透過useState

何時使用？ 1. 第一次運行時 2. 監聽特定值時

元件執行次數舉例：useState會抓原始數值，而useEffect則會抓更新後數值

內層函式取得外層變數 ＝ 閉包

語法：需填入callback function, [條件]
> useEffect( () => {
>   }, [ ] )

 