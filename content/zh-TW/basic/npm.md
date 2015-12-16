## 在 linkit smart 7688 上安裝 Nodejs 套件

### 說明

這個章節我們說明如何在 LinkIt smart 7688 上安裝您所需要的 Nodejs 套件。

若您在安裝 Nodejs 套件上遇到一些問題，也可以參考下面的 `遇到問題列表` 來尋找您的答案。

### 步驟

* 確定版子有跟您的電腦連線
* ssh 進去您的版子
* 進去您的 Nodejs 專案資料夾下
* 比如說我今天想安裝 express 套件，請下：
    
    ```
        npm install express
    ```
* 看到這樣的畫面就是大功告成囉!

Ps. 若您的套件要安裝在 global 的 Nodejs 環境中，請下：
``` 
    npm install express -g
```

### 遇到問題列表

#### Q. npm install 過久或者是連線逾時
A. 連線逾時這部分請先檢查您的網路。npm 執行過久請先檢查 npm install 過程中是否有出現 node-gpy ... 之類的字串，若有是因為需要build 出 binary 檔，這邊 LinkIt smart 7688 上面的 mpu 需要執行較久（因為它不像您的電腦 powerful)，建議遇到這樣的情形時，就需要 openWRT 的 toolchain 去build 出 ipk檔，之後再 88 上使用 opkg install 這個 ipk。相關的 build node-gyp package  Makefile建議參考(https://github.com/openwrt/packages/tree/master/lang/node-serialport) 
    
        

    