`v-on` 是 Vue.js 的事件綁定指令，用來監聽 DOM 事件（如 `click`、`submit` 等）並觸發相應的 JavaScript 方法或回呼函數。
```html
<button v-on:click="increment">Increment</button>
```

在這個範例中：

- 當 `button` 被點擊時，Vue 會呼叫 `increment` 方法。

#### 簡寫

`v-on` 可以縮寫為 `@`，例如 `v-on:click` 可以寫成 `@click`。

#### 常見應用

- 監聽點擊事件、提交事件或其他使用者互動事件，並執行對應的業務邏輯。
- 配合其他指令，如 `v-model` 進行表單驗證或提交。
	`v-on` 是事件驅動的，當用戶觸發事件時執行特定行為。

