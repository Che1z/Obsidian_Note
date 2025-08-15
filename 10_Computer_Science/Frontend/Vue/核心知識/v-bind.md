`v-bind` 是 Vue.js 的單向數據綁定指令，用來將元素的屬性與 Vue 的數據綁定。
`v-bind` 可以綁定任意屬性，比如 `href`、`src`、`class`、`style` 等。

```html
<img v-bind:src="imageUrl" alt="Image">
```

在這個範例中：

- `imageUrl` 是 Vue 實例中的一個數據屬性。
- 當 `imageUrl` 的值改變時，`img` 標籤的 `src` 屬性會隨之改變。

#### 簡寫

`v-bind` 可以縮寫為 `:`，例如 `v-bind:src` 可以寫成 `:src`。

#### 常見應用

- 動態設置圖片路徑或連結。
- 綁定 `class` 或 `style` 屬性，用於動態樣式的設定，例如根據狀態改變元素的顏色或顯示樣式。
	`v-bind` 是單向的，從數據流向 DOM 元素。