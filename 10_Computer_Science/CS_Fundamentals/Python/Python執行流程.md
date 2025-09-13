# Python 程式碼執行流程

## 總結

Python 程式碼的執行過程並非直接被 CPU 讀取，而是經過一道轉譯程序。簡單來說，流程如下：

**Python 原始碼 (.py) -> 位元組碼 (Bytecode) -> Python 虛擬機 (PVM) -> 呼叫 C 函數 -> 執行**

---

## 詳細步驟

1.  **編譯 (Compilation)**
    *   當你執行一個 Python 程式時，Python 直譯器 (Interpreter) 會先將你的 `.py` 原始碼編譯成「位元組碼 (Bytecode)」。
    *   位元組碼是一種低階、但與平台無關 (Platform-Independent) 的中間指令集。
    *   為了效能，直譯器會將編譯後的位元組碼快取 (Cache) 起來，存成 `.pyc` 檔案。如果原始碼沒有變動，下次執行時就可以直接載入 `.pyc`，跳過編譯步驟。

2.  **執行 (Execution)**
    *   編譯完成後，這些位元組碼會被送到「Python 虛擬機 (Python Virtual Machine, PVM)」中。
    *   PVM 是 Python 的核心執行引擎，它是一個迴圈，會逐一讀取並詮釋 (Interpret) 位元組碼指令。

3.  **呼叫 C 函數 (C Function Calls)**
    *   標準的 Python 直譯器是 CPython (用 C 語言開發的)。
    *   因此，PVM 本身就是一個被編譯好的 C 程式。
    *   當 PVM 執行到某個位元組碼指令時 (例如 `BINARY_ADD` 代表加法)，它會去呼叫一個對應的 C 語言函數來完成實際的 CPU 層級操作。

這個設計讓 Python 能夠跨平台執行：只要某個平台有對應的 PVM，同一份 Python 位元組碼就可以在上面執行。
