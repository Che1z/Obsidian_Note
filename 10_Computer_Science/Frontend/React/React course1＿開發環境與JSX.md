#react #前端 #六角

[JSX 差異攻略 (notion.site)](https://bejewled-air-4cb.notion.site/JSX-0d922f32891741718a60a7e13a2849fc)


上集：28：00 (建立完環境)

## 章節核心

- Vite 基本架構
- 
- JSX 結構說明
React版型工具
    - JSX 常見不同的變體
- useState 與 React 的關係

### [](https://hackmd.io/Fqis2SLcTae2FA8-0x72ZA#Vite-%E5%9F%BA%E6%9C%AC%E7%B5%90%E6%A7%8B "Vite-基本結構")Vite 基本結構

- src：會被編譯的程式碼(main.jsx是共同進入點：其餘資料需和其產生關聯才會連動)
- public：不編譯的程式碼
- node_modules：專案相關延伸套件

→ 原始碼解說

→ 指令解說：

- npm run dev
- npm run build

→ **清空，建立自己第一個元件**

1. 清空 App.jsx
2. 元件就是函式，return 後方接 jsx（html）
3. 匯出元件 export default

→ 建立元件口訣（建立三步驟，上集37:00）

1. 使用函式(function)建立，大寫開頭命名
2. return JSX
3. export default (匯出該function)

> 有些設計模式會建議使用 Name Export，在本次課程均僅使用 Default Export

### [](https://hackmd.io/Fqis2SLcTae2FA8-0x72ZA#JSX "JSX")JSX

- 為什麼要用 JSX，可以在 React 插入 `{ }` JavaScript

有什麼用？

1. 可以在 JS 環境中寫 HTML、可以在 HTML 中混寫 JS（但JSX本質仍然是JS）

[JSX 差異攻略 (notion.site)](https://bejewled-air-4cb.notion.site/JSX-0d922f32891741718a60a7e13a2849fc)

1. 可以傳入變數：使用{}填入變數即可，填入內容需要為表達式(expression會return數值)
3. 可以進行運算
4. **可以插入多個內容**
    1. 陣列手法
    2. 物件手法

### [](https://hackmd.io/Fqis2SLcTae2FA8-0x72ZA#React-Hook "React-Hook")React Hook (下集：22:00)

- 沒有 React Hooks 有什麼問題：會無法渲染，常用Hook (useState)
- 基本 React Hooks 用法介紹
    1. 點擊觸發（onClick）
    2. input 輸入值（onChange）
    3. 函式觸發（HandleOnChange）
- 關注點分離的寫法

怎麼練習 useState

1. 將資料轉回狀態
2. 操作狀態

(https://hackmd.io/Fqis2SLcTae2FA8-0x72ZA#%E4%BD%9C%E6%A5%AD%EF%BC%9A "作業：")


[[React course2]]
