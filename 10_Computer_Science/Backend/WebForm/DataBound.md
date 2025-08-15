發生順序：
1. `DataBinding` 事件：
    - 發生在 `PreRender` 之前。
    - 在這個事件中，控制項還未獲取數據，用於設置控制項的屬性或進行一些與數據無關的初始化工作。
2. <mark style="background: #FFB86CA6;">RowCreated（GridView）和 ItemCreated（其他控制項）</mark>事件：
    - 發生在 `DataBinding` 之前，通常在 `Init` 階段。
    - 用於處理那些沒有產生鍵結的內容，例如在動態添加控制項。
3. <mark style="background: #FFB86CA6;">RowDataBound（GridView）和 ItemDataBound（其他控制項）</mark>事件：
    - 發生在 `DataBinding` 之後，但在 `PreRender` 之前。
    - 用於格式化資料、設置樣式、動態調整控制項的內容等。
    - 在這個事件中，每一行（或每一個項目）的數據都已經繫結到相應的控制項。
4. `DataBound` 事件：
    - 發生在 `PreRender` 之前。
    - 表示整個數據繫結過程已經完成，所有的數據都已經成功繫結到控制項。