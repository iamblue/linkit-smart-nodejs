## 使用 MCS + firmata 控制 LED

### 前言

請先使用完畢 [之前的章節](/content/zh-TW/cloud/MCSjs.md)

### 電路圖



### 步驟

* 編輯之前章節的 app.js( 把原來的內容清空 )
* :
    ```
        var ledPin = 13;         
        var firmata = require('firmata');     
        var mcs = require('mcsjs');                
        var board = new firmata.Board("/dev/ttyS0", function(err) {                                                                                             
            if (err) {                             
                console.log(err);                          
                board.reset();                             
                return;                         
            }                                                          console.log('connected...');
            console.log('board.firmware: ', board.firmware);   
            board.pinMode(ledPin, board.MODES.OUTPUT);
            var myApp = mcs.register({
                deviceId: 'Input your deviceId',
                deviceKey: 'Input your deviceKey',
            });
            myApp.on('LED_control', function(time, data) {
                console.log('blink');
                console.log(data);
                if(Number(data) === 1){
                    board.digitalWrite(ledPin, board.HIGH);
                } else {
                    board.digitalWrite(ledPin, board.LOW);
                }
            }); 
        });   
    ```
* 存檔成功後執行 node app
* 
* 完成!