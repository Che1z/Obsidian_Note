#WEB #前端 #網路基本原理

網域名稱系統 (Domain Name Servers)，是一種轉換IP和URL的服務。

>URL <--> IP (via DNS)

IP是真正的網址，其為一串特殊數字(e.g. 63.245.215.20)，由四個範圍的0~255數字組成

Why:
會需要DNS是因為記數字不容易，若使用URL(e.g. mozilla.org)查詢會更簡單

How:
運作流程：輸入URL --> [[瀏覽器]]前往DNS查看IP --> 瀏覽器向伺服器送HTTP請求 --> 伺服器送HTTP回覆(200 OK) --> [[瀏覽器]]將封包組合成完整網站並顯示出

