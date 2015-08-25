## 使用 Nodejs 來創建 video streaming 

### 說明

這個章節我們來透過 Nodejs 來創建 video streaming 。

### 須先準備
* webcam: 建議使用 uvc 規格，本 example 拿 logitech M930 camera 來做基本範例。


### 安裝
* 確定 linkit smart 已安裝 mjpg_streamer

### 原理
* 基本上有安裝完成 mjpg-streamer 即可 work
* 在 command line 輸入：
``` bash
> mjpg_streamer -i "input_uvc.so -d /dev/video0 -r 640x480 -f 25" -o "output_http.so -p 8080 -w /www/webcam" &
```
* 在您的 browser 中打開 `http://mylinkit.local:8080/stream.html` 有看到 video 影像即是正常

### 步驟

* 創建 Nodejs 專案
    ```
        > mkdir app && cd app && npm init
    ```
* 安裝 Paparazzo.JS
    ``` 
        > npm install paparazzo --save
    ```
* 創建 app.js
    ```
        > vim app.js
    ```
* 編輯成以下內容
    ``` js
    var Paparazzo = require('paparazzo');
    var http = require('http');
    var url = require('url');

    paparazzo = new Paparazzo({
        host: 'localhost',
        port: 3000,
        path: '/webcam.mjpg'
    });

    var updatedImage = '';

    paparazzo.on('update', function(image) {
        updatedImage = image
        #console.log "Downloaded #{image.length} bytes"
    })
    
    //paparazzo.on('error', function(error){
    //    console.log(error);
    //})
    
    paparazzo.start();

    http.createServer(function(req, res) {
        var data = '';
        var path = url.parse(req.url).pathname;

        if (path === '/camera' && updatedImage) {
            data = updatedImage;
        }
        
        res.writeHead(200, {
            'Content-Type': 'image/jpeg',
            'Content-Length': data.length
        });

        res.write(data, 'binary');
        res.end();
    }).listen(8080)
    
    ```

* 打開你的 browser 輸入 `http://127.0.0.1:8080/camera` 即可看到成果囉!

    