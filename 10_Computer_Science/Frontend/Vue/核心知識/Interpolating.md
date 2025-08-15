插值是 Vue 中最基本的用法之一。它允許你將數據綁定到 HTML 模板中。最常見的插值語法是使用「雙大括號」(`{{ }}`)包裹一個表達式:


``` HTML
<span>訊息: {{ msg }}</span>
```

在這個例子中,`msg` 是 Vue 實例中定義的一個數據屬性。當 Vue 實例的 `msg` 屬性發生變化時,插值表達式中的值也會自動更新。

除了在標籤文本中使用插值,你還可以在 HTML 元素的屬性中使用插值:



```HTML
<div v-bind:id="dynamicId"></div>
```

在這裡,`dynamicId` 是一個 Vue 實例中的屬性,它的值會被動態地綁定到 `id` 屬性上。

Vue 的插值還支援一些基本的 JavaScript 表達式,比如數學運算、三元運算符等:


``` HTML
<span>{{ number + 1 }}</span> 
<span>{{ isAdmin ? '管理員' : '使用者' }}</span>
```

總的來說,插值是 Vue.js 中非常基本和重要的概念。
它讓我們可以將數據動態地渲染到 HTML 模板上,從而實現了 View 和 Model 的雙向綁定。