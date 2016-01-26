## Let MCS control LinkIt smart 7688 by using MCSjs

### Prerequisite

Please go through [this tutorial](https://mcs.mediatek.com/resources/latest/tutorial/getting_started) . It will guide you to create a test device in MCS. The device contains one on/off control type and one data channel with data channel ID named LED_control.

Note: After the test device is created in MCS,  we need the deivceId and deviceKey on the right upper corner of device detail page. The  deivceId and deviceKey will be used in the following steps.

### Steps

* Check the connection of linkit smart 7688.
* ssh into it.
* Create a folder and go into that folder, and do npm initialization:
    ``` 
        mkdir app && cd app && npm init
    ```
* Install MCSjs modules:
    ``` 
        npm install mcsjs
    ```
* Edit app.js:
    ```
        vim app.js
    ```
* input the content:

``` js
var mcs = require('mcsjs');

var myApp = mcs.register({
    deviceId: 'Input your deviceId',
    deviceKey: 'Input your deviceKey',
});
// Input the deviceId and deviceKey mentioned above.

myApp.on('LED_control', function(data, time) {
    if(Number(data) === 1){                     
        console.log('blink');
    } else {
        console.log('off');
    }
}); 
```

* Save and run node app
* Go back to MCS screen, and press the switch button on the data channel below.
    ![](螢幕快照 2015-09-03 下午3.01.14.png)
    ![](螢幕快照 2015-09-03 下午3.03.10.png)
* Switch to command line, and you will see:
    ```
        blink!
    ```
* The LinkIt smart 7688 and MCS are successfully connected if the above step works fine.

### We will control real LED light though the connection between  MCS <-> LinkIt smart 7688 <-> LED (by firmata package).
