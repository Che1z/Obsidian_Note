# 圖 (Graph)
在計算機科學中，圖是一種由「頂點」(Vertices) 和「邊」(Edges) 組成的非線性資料結構。邊連接頂點，用來表示物件之間的關係。

## 圖的類型
- **無向圖 (Undirected Graph):** 邊沒有方向，如果頂點 A 和 B 之間有邊，則可以從 A 到 B，也可以從 B 到 A。
- **有向圖 (Directed Graph):** 邊有方向，從頂點 A 到 B 的邊不代表可以從 B 到 A。
- **加權圖 (Weighted Graph):** 每條邊都分配了一個權重或成本。
- **無權圖 (Unweighted Graph):** 所有的邊都沒有權重。

## 表示方式
- **鄰接矩陣 (Adjacency Matrix):** 使用二維矩陣來表示頂點之間的連接。`matrix[i][j] = 1` 表示頂點 i 和 j 之間有邊。
- **鄰接串列 (Adjacency List):** 為每個頂點維護一個包含其所有相鄰頂點的列表。

## 常見演算法
- **圖的遍歷:**
  - **廣度優先搜尋 (Breadth-First Search, BFS):** 從一個頂點開始，逐層訪問其所有鄰居。
  - **深度優先搜尋 (Depth-First Search, DFS):** 從一個頂點開始，盡可能深地探索一條路徑，直到無法繼續才回溯。
- **最短路徑演算法:**
  - **Dijkstra 演算法:** 計算單一來源到所有其他頂點的最短路徑（適用於無負權重的圖）。
  - **Bellman-Ford 演算法:** 計算單一來源到所有其他頂點的最短路徑（可處理負權重）。
- **最小生成樹 (Minimum Spanning Tree, MST):**
  - **Prim 演算法**
  - **Kruskal 演算法**
