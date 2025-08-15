Flex items可設定常見屬性包含：
1. flex-grow (成長)：指定如何將flex container中的剩餘空間(remaining space)分配給flex items。該屬性可以設定每個flex item的彈性增長因子(grow factor)，該值範圍是[0, 無限]。
   剩餘空間：flex container大小減去flex item大小的總和。
   剩餘空間分配大小：  看個元素的彈性增長因子數值 (按照比例分配)
   
2. flex-shrink (縮小)：定義flex item在必要時收縮的能力(預設值: 1)
3. flex-basis：定義再分配剩餘空間前元素的默認大小。Flex container空間會先分配給flex-basis，有剩餘再按照flex-grow分配。
    - flex-basis可以是長度(例如20%、5rem)或其他關鍵字。
    - flex-basis僅適用於flex container的main axis，當flex-direction為row時，flex-basis是設定flex item的width大小。反之為column時，則是設定flex item的height大小。
 
 上述1~3屬性，可透過shorthand property (flex)一次設定grow, shrink以及basis
 4. align-self：設定「單個」flex item的對齊方式(而非使用[[flex container]]flex container的align-items設定方式)

