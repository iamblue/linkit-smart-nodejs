##在 linkit smart 上 run 第一隻 Hello wolrd 程式

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
        > vim app.js
    ```
* 在 app.js 內容中按下 i 鍵後寫：
    ``` js
        var fs = require('fs');
        fs.readdir('/Media/SD-P1', function (err, data)         {
            if (err) throw err;
            console.log(data);
        });
        
    ```
* 按下 ESC 鍵，再輸入 wq! 完成儲存後離開
* 輸入 node app.js 即可看到成果囉! 


    

        

    