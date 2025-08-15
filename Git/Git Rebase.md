
``` Git
# 1. 確保你在自己本地的分支上
git checkout feature/xxx

# 2. 先抓取遠端更新（不會自動合併）
git fetch origin

# 3. 以遠端的 dev 分支為基準 rebase
git rebase origin/dev
```
![[Pasted image 20250606162156.png]]

---

## 更改 Commit 訊息

如果你想修改某個 commit 的訊息，可以使用 `git rebase -i`。

1.  **啟動互動式 Rebase**

    假設你要修改最近 3 個 commit 中的某一個，可以執行：
    ```bash
    git rebase -i HEAD~3
    ```

2.  **進入 Vim 編輯模式**

    執行指令後，會進入 [[vim]] 文字編輯器，畫面會顯示一個列表，包含你選擇的 commit。

    ```
    pick 1a2b3c4 commit message 1
    pick 5d6e7f8 commit message 2
    pick 9g8h7i6 commit message 3

    # Rebase ...
    #
    # Commands:
    # p, pick <commit> = use commit
    # r, reword <commit> = use commit, but edit the commit message
    # e, edit <commit> = use commit, but stop for amending
    # s, squash <commit> = use commit, but meld into previous commit
    # ...
    ```

3.  **標記要修改的 Commit**

    在你想修改的 commit 前面，將 `pick` 改成 `reword` (或 `r`)。

    例如，要修改 "commit message 2"：
    ```
    pick 1a2b3c4 commit message 1
    reword 5d6e7f8 commit message 2
    pick 9g8h7i6 commit message 3
    ```

4.  **儲存並離開**

    修改完後，儲存並離開 Vim (在正常模式下輸入 `:wq`)。

5.  **修改 Commit 訊息**

    Vim 會再次開啟，讓你修改該 commit 的訊息。修改完後，再次儲存並離開 (`:wq`)。Git 就會完成 rebase。
