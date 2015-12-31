## Use MCS + firmata to control LED

### Prerequisite

Please finish [previous chapters]/content/en/cloud/MCSjs.md).

### Circuit Diagram

Please connect the hot wire of LED to D13.

### Steps

### MCU Side

* Open Arduino IDE
* copy the code from this site  https://gist.github.com/edgarsilva/e73c15a019396d6aaef2
* Burn the code into Arduino

### MPU Side
* Confirm the connection to LinkIt smart 7688.
* ssh into it.
* Replace the previous content of app.js with the following:
    ```js
        var ledPin = 13;         
        var firmata = require('firmata');     
        var mcs = require('mcsjs');                
        var board = new firmata.Board("/dev/ttyS0", function(err) {
            if (err) {                             
                console.log(err);                          
                board.reset();                             
                return;                         
            }
            console.log('connected...');
            console.log('board.firmware: ', board.firmware);   
            board.pinMode(ledPin, board.MODES.OUTPUT);
            var myApp = mcs.register({
                deviceId: 'Input your deviceId',
                deviceKey: 'Input your deviceKey',
            });
            myApp.on('LED_control', function(data, time) {
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
* Save file, and run node app.
* Press the switch in MCS, and the LED will change with it.
* We have done here!
