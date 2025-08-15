2024/10/29


Point Coordination Function


Ｑ：如何做到頻寬的保留預約？

	PCF 通過 Polling 和較短的 PIFS 時間達到優先傳輸的需求


![[Pasted image 20241029152038.png]]
PCF模式下，**Point Coordinator (PC)** 是負責在非競爭周期內管理通訊的控制點。
PC通常由**接入點（Access Point, AP）** 來扮演。
AP具備管理和協調功能，能夠確保在非競爭周期（Contention-Free Period, CFP）中所有的無線裝置都不會相互干擾。

**PC的必要條件或建議條件**：

- **具備AP角色**：PC必須是網路中的AP，這樣它才能管理整個無線區域網路中的所有終端設備。
- **具備足夠的資源**：作為PC的設備通常需要較強的處理能力和較穩定的連接品質，以便能夠有效地管理並指導所有的終端設備。
- **支援PCF模式**：並非所有的AP都支援PCF模式，因為PCF並不是強制性標準。
  因此，PC必須支援PCF功能，才能啟動和維護非競爭週期。

![[Pasted image 20241029152103.png]]
- **非競爭周期（Contention-Free Period, CFP）**：在這段期間內，PC (通常是AP) 會控制頻寬的使用，並直接分配頻寬給不同的終端設備。
  終端設備在這段期間不會自行發起通訊，因此可以避免碰撞。
    
- **競爭周期（Contention Period, CP）**：在這段期間，所有終端設備會透過 **CSMA/CA 協定來競爭頻寬。
  
  
  ![[Pasted image 20241029154028.png]]


CF-Down：Coordinator point下傳資料到station
CF-Up : Station上傳資料到Coordinator point
![[Pasted image 20241029155512.png]]

- **CF-Poll Subtype Data Frame**：
    
    - **用意**：在非競爭周期（Contention-Free Period, CFP）內，**Point Coordinator (PC)** (通常是AP) 會輪詢各個終端設備，詢問它們是否有要傳輸的資料。
    - **過程**：PC 向每個設備發送一個 CF-Poll Frame，授權它們在 CFP 期間進行傳輸。只有被 PC 輪詢的設備可以在 CFP 期間傳輸數據，這樣可以避免碰撞並確保頻寬的有效使用。
    - **操作邏輯**：如果 PC 向某個設備發送 CF-Poll Frame，但該設備沒有要傳輸的數據，則該設備會回應 PC 表示不需傳輸，然後 PC 會輪詢下一個設備。
- **CF-End Frame**：
    
    - **用意**：當 CFP 期間結束時，PC 會發送一個 CF-End Frame，告知所有終端設備 CFP 已經結束，接下來進入競爭周期（Contention Period, CP）。
    - **功能**：CF-End Frame 的目的是**通知所有設備可以恢復 CSMA/CA 的競爭模式**，並且讓原本等候的設備可以開始依照 DCF 規則進行數據傳輸。

![[Pasted image 20241029160745.png]]

- **PCF 模式的優先級**：PC 使用 PIFS 進行傳輸，優先權高於 DCF 模式的工作站（因為 PIFS < DIFS）。
- **NAV 的設置**：在每次 CFP 開始時，PC 通過設定 NAV 為 CFP(非競爭週期) 的時長，讓範圍內的所有設備避免在 CFP 期間傳輸。
- **CF-End Frame 的作用**：在 CFP 結束時，PC 發送 CF-End Frame，使所有端點的 NAV 重置，並恢復到競爭模式。
- **Superframe**：一個 superframe 包含 CFP 和 CP 兩個週期，先由 PC 控制的非競爭 CFP，再切換到讓所有工作站競爭的 CP。