Json-Web Token
後端傳遞一個`JSON`資料（已透過`Base64`）轉譯過後，前端再透過`Base64`轉譯回原先內容。

`JWT`有三個部分，分別透過<mark style="background: #FFB86CA6;">點（.）</mark>分隔：
1. Header (標題)：包含加密演算法、token類型
``` JSON
{
  "alg": "HS256",
  "typ": "JWT"
}
```
	1. Payload (內容)：主要存放包含 JWT規範的標準數據及自定義數據
```JSON
{
  iss:提供者 （標準數據）,
  sub:主旨 (標準數據),
  exp:過期時間（標準數據）,
  iat:創建時間 （標準數據）,
  score: 80 (自定義數據)
}
```   
   
3. Signature (簽名)：存放對header 及 payload加密的簽章演算法的字符串(ex: HS256，HS512 …等)


流程圖：
![[Pasted image 20240502104820.png]]

```
Ｑ：為何會需要轉譯？
Ａ：確保能跨平台、裝置溝通，定義好語言的意思
```