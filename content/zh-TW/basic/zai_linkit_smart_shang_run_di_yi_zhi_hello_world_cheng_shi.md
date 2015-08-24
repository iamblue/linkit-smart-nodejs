##在 linkit smart 上 run 第一隻 Hello wolrd 程式

### 說明

這個章節我們來透過 nodejs 來創建第一隻 Hello world 程式

### 步驟

* 把 microSD 插進 Linkit smart 中
* ssh 進去你的 Linkit smart
* 產生一個名為 app 的 forlder
    ``` bash
        > mkdir app
    ```
* 產生 app.js 
    ``` bash
        > vim app.js
    ```
* 在 app.js 內容中按下 i 鍵後寫：
    ``` js
        console.log('Hello world');
        
    ```
* 按下 ESC 鍵，再輸入 wq! 完成儲存後離開
* 輸入 node app.js 即可看到成果:
    ``` bash
        > Hello world
    ```

    

        

    