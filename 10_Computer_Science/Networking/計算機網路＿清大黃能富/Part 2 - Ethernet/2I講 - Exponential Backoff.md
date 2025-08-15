2024/10/25

`Adaptor`: 網路介面卡
![[Pasted image 20241025173600.png]]
連續碰撞，代表<mark style="background: #FFF3A3A6;"> 網路Loading </mark>較重，因此等待時間會較久

第一次等待時間<mark style="background: #FFF3A3A6;">需要是</mark>隨機的，否則等到下一次也只是碰撞（碰撞 -->等待 -->碰撞）
![[Pasted image 20241028100123.png]]


碰撞最大允許次數為`16`次，若是超過即不再重新發送
k的話，則是會隨著每次發生碰撞後數值增增加`1`，上限是`10`(2^10 - 1 = 1023)

