# Doubly Linked List (雙向鏈結串列)

Doubly Linked List 是 [[Singly Linked List]] 的一種延伸。它的每個節點 (Node) 包含三個部分：

1.  **資料 (Data)**：儲存該節點的實際數值。
2.  **下一個節點的指標 (Next Pointer)**：指向下一個節點。
3.  **上一個節點的指標 (Previous Pointer)**：指向上一個節點。

頭節點 (Head) 的 `Previous Pointer` 指向 `null`，尾節點 (Tail) 的 `Next Pointer` 也指向 `null`。

### 特性

*   **雙向性**：可以從頭到尾，也可以從尾到頭進行遍歷。從任何一個節點，都可以快速找到其前一個和後一個節點。
*   **操作靈活**：
    *   在給定節點「之前」或「之後」插入新節點都非常快 (`O(1)`)。
    *   刪除一個給定的節點也是 `O(1)`，因為可以直接透過該節點找到前後節點來重新連接它們。
*   **空間成本較高**：相較於單向鏈結串列，每個節點都需要額外儲存一個 `Previous Pointer`，記憶體開銷較大。
