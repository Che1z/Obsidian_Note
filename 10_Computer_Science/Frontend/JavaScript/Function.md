以數學函數為例:
f(x) = 3x + 6，x稱為是parameter。當函數為f(5)時，5被稱為argument。

除了JS內建的function外(e.g. alert()、prompt()...)，我們可以自行定義自己的function。
Function由一連串的程式碼組合，用來完成任務或計算值。

JS Function宣告語法：[ ]代表可放可不放
![[Pasted image 20230820205826.png]]

在JS Function中，若沒有return語句，function將返回undefined(JS的function默認的return value)，若要返回默認值以外的值，函數必須具有要有指定返回的return語句值。

return語句會結束函示執行並指定要返回給函數調用者的值，任何放在return下的程式碼都不會被執行。

每個JS函數實際上都是一個物件(每個function有instance properties以及instance methods)

---
[[時間複雜度]]

---
[[Function Expression]]

[[Arrow function]]