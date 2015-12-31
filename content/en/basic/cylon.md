## Controlling LED with Cylon.js

![](cylon.png)

### Aim

(Notice: Before studying this section, be sure to finish firmata section)

In this section, we are going to use the famous open source project `Cylon.js` on Nodejs to control LED.

### Prerequisites

#### Control LED needs

(as the firmata section)
* LED x 1
* Resistor x 1
* A few DuPont wires

#### Circuit diagram
(as the firmata section)

### Steps

#### MCU side
* Open your Arduino IDE. 
* Copy the contents in this URL: https://gist.github.com/edgarsilva/e73c15a019396d6aaef2 
* Burn into Arduino.  

#### MPU side

* ssh into LinkIt Smart 7688.

* Generate a folder named 'app':
    ``` bash
        > mkdir app && cd app
    ```

* Generate `app.js`:
    ``` bash
        > vim app.js
    ```
    
* Install `cylon`, `cylon-firmata`, `cylon-gpio`, `cylon-i2c` package:
    
    * Due to the same reason as firmdata, node-gyp actions will cause too long running time on LinkIt Smart 7688 Duo. So we recommend using the same way as the firmata to install these four packages.
    * For detailed procedures, please refer to firmata section.
    
    
* After confirming above four kits is installed at /node_modules folder, add `app.js` in the root directory (`/app`)：
    ```
        vim app.js
    ```
* After pressing the `i` key, enter:
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
* Press `ESC`, then enter `wq!` to save and leave.
* Enter `node app.js` to see see lights on the board flashing.
* Done!
    

        

    