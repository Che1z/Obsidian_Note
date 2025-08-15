`v-model` 是 Vue.js 提供的<mark style="background: #FFF3A3A6;">雙向</mark>數據綁定指令，用於在表單元素
（例如 `<input>`、`<textarea>`、`<select>`）與 Vue 元件的數據之間同步數據。

``` html
<input v-model="message" />
<p>{{ message }}</p>
```

在這個範例中：

- 當使用者在 `input` 中輸入內容時，`message` 會即時更新。
- 當 `message` 的值變動時，`input` 的值也會隨之更新，實現雙向數據綁定。

`v-model` 是 [[v-bind]] 和 [[v-on]] 的語法糖，具體來說：

- 綁定 `value` 屬性（`v-bind:value="message"`）。
- 監聽 `input` 事件（`v-on:input="message = $event.target.value"`），當 `input` 事件觸發時，更新綁定的數據。

#### 常見應用

- 表單數據綁定，例如用戶名、密碼、勾選框的選擇等。
- 動態表單元件，根據使用者的輸入即時更新數據。
	`v-model` 是雙向的，數據和 DOM 元素之間可以相互影響。