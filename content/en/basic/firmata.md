## Controlling LED with firmdata

### Aim

#### Caution: Methods described in this section only applies to LinkIt smart 7688 Duo. LinkIt smart 7688 is not allowed to use.

Preface: LinkIt Smart 7688 has two chips, one is the MPU (7688) capable to run linux; the other one is the Arduino MCU. For Node.js developers, it is desired to run Node.js app on the MPU. Arduino MCU is directly controlled by this app. As as result, we are going to use Node.js firmdata package to communciate between MPU and Arduino MCU.


### Prerequisites

#### Control LED requires

* LED x 1
* Resistor x 1
* A few DuPont wires

#### Please install circuit first:

![](firmata_bb.jpg)

### Steps

#### MCU side
* Open your Arduino IDE. 
* Copy contents in this URL: https://gist.github.com/edgarsilva/e73c15a019396d6aaef2 
* Burn into Arduino  

#### MPU side

* ssh into your `LinkIt smart 7688 Duo`.

* Generate a folder named `app`.
    ``` bash
        > mkdir app && cd app
    ```
    
* Install `firmata`

    Notice! Because there are some compilation procedures during npm install, which will cause too long running time on LinkIt smart 7688 Duo, it is not recommended to use `npm install` method for firmata package.
    
    So we will first generate a testfirmdata folder on host side (your computer).
    
    ```
        mkdir testfirmata && cd testfirmata
    ```
    
    Then execute: 
    
    ```
        npm init 
    ```
    
    Install `firmata`:
    
    ```
        npm install firmata --save
    ```
    
    Because of a dependent package inside `firmata`, it will generate the compilation spec file according on your computer's spec during installation on your computer. However, the MIPS compilation spec file has already been installed on LinkIt Smart 7688 Duo, so we must erase this package manually:
    ```
        rm -rf ./node_modules/firmata/node_modules/serialport/
    ```
    
    Package `firmata` folder:
    
    ```
        tar -cvf ./firmata.tar ./node_modules/firmata
    ```
    
    Transfer the tar file into your `LinkIt smart 7688 Duo` board.
    
    ```
        scp ./firmata.tar root@mylinkit.local:/root/app/node_modules/
    ```
    (If something like `can not find node_modules folder` appears, please return to `/app` folder on your board and make a folder named `node_modules`: `mkdir node_modules`)
    
* Go back to your board's terminal.
* Back to `/testfirmata`:
* Enter `node_modules` folder: `cd node_modules`
* Unpack the tar file: `tar -xvf ./firmata`
* Back to `/testfirmata`：`cd ..`
* generate a `app.js` file:
    
    ```
        vim app.js
    ```
    
* Paste the following content:

``` js
console.log('WWW blink start ...');

var ledPin = 13;
var firmata = require('firmata');

var board = new firmata.Board("/dev/ttyS0", function(err) {
    if (err) {
        console.log(err);
        board.reset();
        return;
    }

    console.log('connected...');
    console.log('board.firmware: ', board.firmware);

    board.pinMode(ledPin, board.MODES.OUTPUT);

    var url = require('url');
    var http = require('http');

    http.createServer(function(request, response) {
        var params = url.parse(request.url, true).query;
        try {
            if (params.value.toLowerCase() == 'high') {
                board.digitalWrite(ledPin, board.HIGH);
            } else if (params.value.toLowerCase() == 'low'){
                board.digitalWrite(ledPin, board.LOW);
            }
        } catch(e) {
        
        }
        response.writeHead(200);
        response.write("The value written was: " + params.value);
        response.end();
    }.bind(this)).listen(8080);

    console.log('Listening on port 8080 ...');
});
```
    
* Execute `app.js`.  
    ``` 
        node app
        
    ```
* Press `ESC`, then enter `wq!` to save and leave.
* Open your browser:

    * `http://mylinkit.local?value=high` (led-on)
    * `http://mylinkit.local?value=low` (led-off)
    

        

    