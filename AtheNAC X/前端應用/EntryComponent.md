#全域import方式 

``` vue
<template>

  <VCard>

    <VCardText class="pb-2">

      <h5 class="text-h5">

        {{ $t('Templete_Module.welcome') }}

        <p>asd</p>

      </h5>

      <p class="mb-0 text-sm text-disabled">

        {{ $t('Templete_Module.hello', { name: 'Leo' }) }}!!

      </p>

    </VCardText>

  </VCard>

</template>
  
<script setup lang="ts">

</script>
```

`VCard`和`VCardText`是透過[[全域註冊]]的方式來使用的，通常在專案的主要設定檔（如 `main.js` 或 `plugins/vuetify.js`）中進行 Vuetify 的安裝和配置。

這就是為什麼在組件檔案中可以直接使用這些 V- 前綴的組件，而不需要額外的 import 語句。

---

專案全局註冊機制 : 

1. 主要入口文件 `main.ts` 顯示這個專案使用了 `mainui-lib` 這個庫：
``` typescript
import mainui from 'mainui-lib';
import 'mainui-lib/dist/style.css';
```

``` json
"types": [
  "mainui-lib",
  "mainui-lib/vuexy",
  "mainui-lib/vuetify",  // Vuetify 組件的類型定義
  "mainui-lib/pinia",
  "mainui-lib/apexcharts"
]
```

2. 組件的註冊過程：
    
    - `mainui-lib` 庫內部已經配置和註冊了 Vuetify 組件
    - 當應用啟動時，這些組件被全局註冊，使得所有 Vue 組件都可以直接使用 V- 前綴的 Vuetify 組件
    - 這就是為什麼在 `EntryComponet.vue` 中可以直接使用 `VCard` 和 `VCardText` 而不需要額外導入

