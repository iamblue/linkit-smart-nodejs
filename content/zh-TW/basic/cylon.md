## 使用 cylon.js 來控制 LED

### 說明

（注意：在學習這章節之前，請務必先閱讀完 firmata 章節）

這個章節我們來透過 nodejs 上著名的開源專案 cylon.js 來控制 LED 。

### 須先準備

#### 控制 LED 須準備
* LED x 1
* 電阻 x 1
* 杜邦線數條


### 步驟

* 先將

* 產生一個名為 app 的 forlder
    ``` bash
        > mkdir app && cd app
    ```

* 產生 app.js 
    ``` bash
        > vim app.js
    ```
    
* 安裝 cylon, cylon-firmata, cylon-gpio, cylon-i2c:
    
    * 由於以上套件跟安裝 firmata 一樣會遇到 npm install 
    ```
        > npm install firmata --save
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

    

        

    