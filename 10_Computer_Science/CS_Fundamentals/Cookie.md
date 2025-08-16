Cookie是在Web Server和瀏覽器之間，伴隨要求(Request)和網頁傳送的一小段文字。
就像是名片，呈現相關識別以協助程式了解使用者，並知道如何繼續。

1. 建立Cookie時，會需要指定name和value，因此名字需要不可重複，否則會被覆蓋。
2. Cookie若是沒設到期時間的話，就會變成Session Cookie，當用戶關閉瀏覽器時就會被刪除
3. 單一Cookie設定複數值
``` C#
// Cookie名為userInfo，並具有userName和lastVisit兩個值

// 法一：
Response.Cookies["userInfo"]["userName"] = "Jeremy";
Response.Cookeis["userInfo"]["lastVisit"] = DateTime.Now.ToShortDateString();

// 法二： aCookie為HttpCookie實例化名稱、userInfo則為該實例所代表的 Cookie名稱
HttpCookie aCookie = new HttpCookie("userInfo");
aCookie.Values["userName"] = "Jeremy";
aCookie.Values["lastVisit"] = DateTime.Now.ToShortDateString();

Response.Cookies.Add(aCookie);
```

4. Cookie是存放在用戶端硬碟，而非伺服器端