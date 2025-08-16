基本有Post、Get、Put、Delete這四種，以符合CRUD需求
C: Create (Post)
R: Read (Get)
U: Update (Put)
D: Delete (Delete)

1. **Post：**
    - 通常用於向伺服器提交資源，用於創建新的資源。
    - 強調的是將客戶端的資料提交到伺服器，以便在伺服器上進行處理和創建新資源。
    - [[非冪等(non-idempotent)]]
1. **Get：**
    - 主要用於從伺服器獲取資源，對資源的操作是安全且幂等的。
    - 不應該對伺服器資源進行修改，主要用於獲取資料，而不對資源狀態進行改變。
    - 冪等(non-idempotent)
1. **Put：**
    - 用於更新現有資源，或在伺服器上創建新的資源（如果不存在）。
    - 與POST不同之處在於PUT的請求是可幂等的，即多次使用相同的請求不應導致不同的結果。
    - 冪等(non-idempotent)
2. **Delete：**
    - 用於刪除指定的資源。
    - 請求的執行應該是幂等的，即對同一資源的多次請求應該具有相同的效果。
    - 冪等(non-idempotent)

---
除基本功能外還有如Patch（非冪等(non-idempotent)）、Options等用法（冪等(non-idempotent)）：
