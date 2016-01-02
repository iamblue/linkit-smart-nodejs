## 使用 LinkIt-smart-gpio 套件來操控 GPIO 

### 說明

這個章節我們來透過 Nodejs 來操控GPIO 。

### 須先準備

#### 控制 LED 須準備
* LED x 1
* 電阻 x 1
* 杜邦線數條

#### 監聽按鈕須準備
* 按鈕 x 1
* 電阻 x 1

## 控制 LED (輸出 GPIO 訊息)

### 步驟
* 將 LED 接上 P8
* ssh 進去 Linkit smart 7688
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


## 監聽按鈕是否按下 (接收 GPIO 訊息) 
### 步驟
    

        

    