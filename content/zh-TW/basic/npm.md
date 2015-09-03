## 在 linkit smart 上安裝 Nodejs 套件

### 說明

這個章節我們說明如何在 Linkit smart 上安裝您所需要的 Nodejs 套件。

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
A. 連線逾時這部分請先檢查您的網路。npm 執行過久請先檢查 npm install 過程中是否有出現 node-gpy ... 之類的字串，若有是因為 l 7688 上面的 mpu 需要執行較久（因為它不像您的電腦 powerful)，建議遇到這樣的情形時，請先在您的電腦上做好npm install某套件，然後再把此套件打包成 tar 檔再用 scp 的方式傳進去您的 l 7688 版子上。
    
        

    