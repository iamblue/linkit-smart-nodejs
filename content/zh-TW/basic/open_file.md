## 打開 microSD 上的檔案

### 說明

這個章節我們來透過 nodejs 來直接讀取 LinkIt smart 7688 上面的 microSD 卡內容。

### 步驟

* 把 microSD 插進 LinkIt smart 7688 中
* ssh 進去你的 LinkIt smart 7688
* 產生一個名為 app 的 forlder
```sh
> mkdir app
```
* 產生 app.js 
```sh
> vim app.js
```
* 在 app.js 內容中按下 i 鍵後寫：

``` js
var fs = require('fs');
// **** 注意 ****
// 1. 下面的 SD-P1 代表的意思是，讀取 SD 卡的第一個磁碟分割
// 2. Linkit smart 上的不論你接 usb host 還是 SD 卡，都一律會在/Media 資料夾下找到
fs.readdir('/Media/SD-P1', function (err, data) {
    if (err) throw err;
    console.log(data);
});
        
```
    
* 按下 ESC 鍵，再輸入 wq! 完成儲存後離開
* 輸入 node app.js 即可看到成果囉! 


    

        

    