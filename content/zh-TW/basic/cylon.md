## 使用 Cylon.js 來控制 LED

### 說明

（注意：在學習這章節之前，請務必先閱讀完 firmata 章節）

這個章節我們來透過 nodejs 上著名的開源專案 cylon.js 來控制 LED 。

### 須先準備

#### 控制 LED 須準備

(跟 firmata 章節一樣)
* LED x 1
* 電阻 x 1
* 杜邦線數條

#### 電路圖
(跟 firmata 章節一樣)

### 步驟

#### MCU 端
* 打開你的 Arduino IDE 
* copy 這網址的內容: https://gist.github.com/edgarsilva/e73c15a019396d6aaef2 
* 燒錄進去 Arduino  

#### MPU 端

* ssh 進去 linkit smart 7688

* 產生一個名為 app 的 forlder :
    ``` bash
        > mkdir app && cd app
    ```

* 產生 app.js :
    ``` bash
        > vim app.js
    ```
    
* 安裝 `cylon`, `cylon-firmata`, `cylon-gpio`, `cylon-i2c` 套件:
    
    * 由於以上套件跟安裝 firmata 一樣，要做一些 compile 的動作，這會造成l 7688 Duo 執行過久，因此我們建議使用當初裝 firmata 的方式一樣安裝以上四個套件。
    * 詳細章節請參考 firmata 章節。
    
    
* 以上四個套件都確認安裝在 /node_modules folder 下後，在根目錄 (/app) 下新增 app.js ：
    ```
        vim app.js
    ```
* 按下 i 鍵後撰寫寫：
    ``` js
        var Cylon = require('cylon');

        Cylon.robot({
            connections: {
                arduino: { adaptor: 'firmata', port: '/dev/ttyS0' }
            },

            devices: {
                led: { driver: 'led', pin: 13 }
            },

            work: function(my) {
                every((1).second(), my.led.toggle);
            }
        }).start();
        
    ```
* 按下 ESC 鍵，再輸入 `wq!` 完成儲存後離開
* 輸入 node app.js 即可看到成果:


* 完成!
    

        

    