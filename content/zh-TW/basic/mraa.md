## 使用 mraa 套件來操控 GPIO 

### 說明

這個章節我們來透過 mraa 來操控GPIO 。

附註：這個範例操控的 LED 燈是版子上的 wifi 那顆。

## 控制 LED (輸出 GPIO 訊息)

### 步驟
* ssh 進去 Linkit smart 7688
* 產生一個專案

    ``` bash
    > mkdir app
    ```

* 用 npm 初始化您的專案
    
``` bash
    > npm init
    ```
    
* 產生一個 app.js 檔案
    
``` bash 
> vim app.js
```
    
* 編輯 app.js 內文
    
``` js
var m = require('mraa');
var ledState = true;
var myLed = new m.Gpio(44);

myLed.dir(m.DIR_OUT);

function periodicActivity() {
    myLed.write(ledState ? 1 : 0);
    ledState = !ledState;
    setTimeout(periodicActivity, 1000);
}
periodicActivity();
```
    
* 就可以看到成果囉!

![demo](http://iamblue.gitbooks.io/linkit-smart-nodejs/content/images/blink.gif)

        

    