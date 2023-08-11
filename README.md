# VueTypeScriptAspNet7.0
visaul studio .17 版本 VueTypeScriptAspNet7.0 

> 嘗試使用預設專案，建立前後端分離專案，並部署至IIS建立服務
>

- node_modules 已刪除，需重新下載
- urlrewrite 請自行放到前臺服務站臺底下
- vueapp 預設使用 vite proxy 加入 changeOrigin: true
- webapi 有自行加入 Cors 設定
- 主要請看：
  - 專案 vueapp >   
    - 轉址設定：vite.config.ts
    -  src > components
      -   頁面：HelloWorld.vue
