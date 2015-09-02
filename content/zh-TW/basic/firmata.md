## 使用 firmata 來控制 LED

### 說明

#### 注意 : 本章節適用於 l 7688 Duo 版子， l 7688 不可以用哦!

前言：l 7688 上面有兩顆晶片，一顆是跑得動 linux 的 MPU ( 7688 )，另外一顆為 Arduino MCU，對於 Nodejs 開發者而言，我們會希望能夠在 MPU 上跑我們的 Nodejs app，透過這個 app 能夠直接控制 Arduino MCU。因此這個章節我們來透過 Nodejs 的 firmata 套件讓 MPU 跟 Arduino MCU 兩邊能夠溝通。


### 須先準備

#### 控制 LED 須準備

* LED x 1
* 電阻 x 1
* 杜邦線數條

#### 請先安裝電路

![](firmata_bb.jpg)

### 步驟

#### MCU 端
* 打開你的 Arduino IDE 
* copy 這網址的內容: https://gist.github.com/edgarsilva/e73c15a019396d6aaef2 
* 燒錄進去 Arduino  

#### MPU 端

* ssh 進去你的 7688

* 產生一個名為 app 的 forlder
    ``` bash
        > mkdir app && cd app
    ```
    
* 安裝 firmata

    注意！因為 npm 安裝 firmata 套件要做一些 compile 的動作，這會造成l 7688 Duo 執行過久，因此不建議在l 7688 Duo版子上使用 `npm install` 方式安裝 firmata 套件。
    
    因此我們先在本機端（你的電腦）先產生一個 testfirmata folder
    
    ```
        mkdir testfirmata && cd testfirmata
    ```
    
    接下來執行： 
    
    ```
        npm init 
    ```
    
    安裝firmata：
    
    ```
        npm install firmata --save
    ```
    
    因為 firmata 內部引用的一個套件(node-serialport) 在電腦上安裝時會產生你電腦規格的 compile 檔，但是這個套件的mips compile檔已經安裝在我們的l 7688 Duo上面，所以我們必須執行把這套件刪除的動作:
    ```
        rm -rf ./node_modules/firmata/node_modules/serialport/
    ```
    
    壓縮 firmata folder：
    
    ```
        tar -cvf ./firmata.tar ./node_modules/firmata
    ```
    
    將壓縮好的檔案傳進你的 l 7688 Duo 版子
    
    ```
        scp ./firmata.tar root@mylinkit.local:/root/app/node_modules/
    ```
    (如果出現 can't find node_modules folder 的字眼，請回到你的版子的 /app folder 產生一個 node_modules 的 folder : `mkdir node_modules`)
    
* 回到你的版子的終端機
* 產生一個 app.js 檔案：
    
    ```
        vim app.js
    ```
    
* 貼上這段內文：
    ``` js
        console.log('WWW blink start ...');

        var ledPin = 13;
        var firmata = require('firmata');

        var board = new firmata.Board("/dev/ttyATH0", function(err) {
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

                if (params.value.toLowerCase() == 'high') {
                    board.digitalWrite(ledPin, board.HIGH);
                } else {
                    board.digitalWrite(ledPin, board.LOW);
                }
                response.writeHead(200);
                response.write("The value written was: " + params.value);
                response.end();
            }.bind(this)).listen(8080);

            console.log('Listening on port 8080 ...');
        });
    ```
* 執行 app.js  
    ``` 
        node app
        
    ```
* 打開你的 browser :

    * 127.0.0.1:8080?value=high 為打開 led
    * 127.0.0.1:8080?value=low 為關掉 led
    

        

    