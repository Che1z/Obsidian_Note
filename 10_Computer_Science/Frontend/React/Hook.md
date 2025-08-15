#react 
Hook其實就是JS function，只是需特別注意以下兩點：
1. 只在最上層呼叫Hook，不要在迴圈、條件式或是巢狀Function內呼叫Hook  
    參考：[React - Hook](https://react.dev/learn/state-a-components-memory#meet-your-first-hook)
    Hooks are functions, but it’s helpful to think of them as unconditional declarations about your component’s needs. 
    You “use” React features at the top of your component similar to how you “import” modules at the top of your file
    
2. 只在React Function中呼叫Hook，例如：在React function component中呼叫Hook
![[Screenshot 2023-08-14 at 9.35.31 PM.png]]

![[Screenshot 2023-08-14 at 9.36.51 PM.png]]

---
Hook方法：
1. [[useState]]
2. [[useEffect]]