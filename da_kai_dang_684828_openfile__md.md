## 打開 microSD 檔案

### 說明

這個章節我們來透過 nodejs 來直接讀取 linkit smart 上面的 microSD 卡內容。

### 步驟

* 把 microSD 插進 Linkit smart 中
* ssh 進去你的 Linkit smart
* 產生一個名為 app 的 forlder
    ```sh
        > mkdir app
    ```
* 產生 app.js 
    ```sh
        > touch app.js
    ```
* 在 app.js 內容中寫
    ``` js
        var fs = require('fs');
        
    ```
    
大功告成!
    

        

    