## 使用 MCSjs 雲端操控 l 7688

### 前言

請先看 [這個教學](https://mcs.mediatek.com/resources/latest/tutorial/getting_started) 在 MCS 中 create 好一個內容只有一個 on/off (control type) 且 data channel ID 名為 LED_Control 的 data channel 的 test device。

我們在 MCS 中 create 出 test device 後，會在該 device detail page 的畫面的右上方得到 deivceId 跟 deviceKey 即為下面步驟的 deviceId 跟 deviceKey。

### 步驟

* 確定跟你的 l 7688 連線
* ssh 進去
* 創建一個資料夾並進去:
    ``` 
        mkdir app && cd app && npm init
    ```
* 安裝 MCSjs modules:
    ``` 
        npm install mcsjs
    ```
* 編輯 app.js:
    ```
        vim app.js
    ```
* 輸入:
    ```
        var mcs = require('mcsjs');

        var myApp = mcs.register({
            deviceId: 'Input your deviceId',
            deviceKey: 'Input your deviceKey',
        });
        // 這邊輸入上述打的 deviceId 跟 deviceKey
        
        myApp.on('GPIO_00', function(time, data) {
            console.log('blink');
            console.log(data);
            if(Number(data) === 1){                          
                board.digitalWrite(ledPin, board.HIGH);
            } else {
                board.digitalWrite(ledPin, board.LOW);
            }
        }); 
    ```
