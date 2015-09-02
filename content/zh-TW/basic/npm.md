## 在 linkit smart 上安裝 Nodejs 套件

### 說明

這個章節我們說明如何在 Linkit smart 上安裝您所需要的 Nodejs 套件。

若您在安裝 Nodejs 套件上遇到一些問題，也可以參考下面的 `遇到問題列表` 來尋找您的答案。

### 步驟

* 請先打開瀏覽器至您的 Web console UI (初始網址是 http://mylinkit.local )
* 點選 Network -> 選擇 station 
* 打上你希望連線的 wifi ssid 跟 password
* 確定版子有跟您所指定的 ap 連線
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
A. 這狀況很大原因是
    
#### Q.
        

    