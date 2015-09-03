## 使用 MCS + firmata 控制 LED

### 前言

請先閱讀完畢 [之前的章節](/content/zh-TW/cloud/MCSjs.md)。

### 電路圖

LED 的火線請接 D13。


### 步驟

### MCU 端

* 打開你的 Arduino IDE 
* copy 這網址的內容: https://gist.github.com/edgarsilva/e73c15a019396d6aaef2 
* 燒錄進去 Arduino  

### MPU 端
* 確認 l 7688 是否已經連接
* ssh 進去
* 編輯之前章節的 app.js ( 把原來的內容清空 )
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
* 按下 MCS 的 switch 後，就可以看到 LED 燈隨著變化囉!
* 完成!