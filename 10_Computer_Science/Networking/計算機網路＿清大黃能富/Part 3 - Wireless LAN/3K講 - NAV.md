2024/10/29

![[Pasted image 20241029143024.png]]


![[Pasted image 20241029143037.png]]
每一段NAV時長都是（資料發送時間 + Ack等待時間）
發送多久封包自身都知道，而Ack則是固定時長
最後一份的封包以及Ack，時長會設為0

![[Pasted image 20241029143146.png]]


![[Pasted image 20241029143157.png]]
即使頻道為空閒狀態（Ack1封包發生意外沒有發送），也必須等到NAV(Fragment 1)時間結束才可發送。 因為其他端點並不知道頻道現況，NAV並沒有也無法更新。



![[Pasted image 20241029143213.png]]

若是封包長度短於RTS_Threshold，則不需用RTS/CTS機制來預約封包避免碰撞

