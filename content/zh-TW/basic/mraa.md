## 使用 mraa 套件來操控 GPIO 

### 說明

這個章節我們來透過 mraa 來操控GPIO 。


## 控制 LED (輸出 GPIO 訊息)

### 步驟
* ssh 進去 Linkit smart
* 產生一個專案
    ``` bash
    > mkdir app
    ```
* 用 npm 初始化您的專案
    ``` bash
    > npm init
    ```
* 安裝 linkit-smart-gpio 套件
    ``` bash
    > npm install linkit-smart-gpio --save
    ```
    
* 產生一個 app.js 檔案
    ``` bash 
    > vim app.js
    ```
* 編輯 app.js 內文
    ``` js
    var gpio = require('linkit-smart-gpio');
    gpio.register(8, 'output'); // 8 means P8

    gpio.low(8);

    // open led after 3 seconds...
    setTimeout(function(){ gpio.high(8) }, 3000);
    ```
* 就可以看到成果囉!

![demo](http://iamblue.gitbooks.io/linkit-smart-nodejs/content/images/blink.gif)

        

    