## 使用 firmata 來控制 LED

### 說明

#### 注意 : 本章節適用於 l 7688 Duo 版子， l 7688 不可以用哦!

前言：l 7688 上面有兩顆晶片，一顆是跑得動 linux 的 MPU (7688)，另外一顆為 Arduino MCU，對於 Nodejs 開發者而言，我們會希望能夠在 MPU 上跑我們的nodejs app，透過這個 app 能夠直接控制 Arduino MCU。因此這個章節我們來透過 Nodejs 的 firmata 套件讓 MPU 跟 Arduino MCU 兩邊能夠溝通。


### 須先準備

#### 控制 LED 須準備
* LED x 1
* 電阻 x 1
* 杜邦線數條

#### 請先安裝電路

![](firmata_bb.jpg)

### 步驟

* 先將

* 產生一個名為 app 的 forlder
    ``` bash
        > mkdir app && cd app
    ```

* 產生 app.js 
    ``` bash
        > vim app.js
    ```
    
* 安裝 firmata

    不建議使用：
    ```
        > npm install firmata --save
    ```
    

    
* 在 app.js 內容中按下 i 鍵後寫：
    ``` js
        console.log('Hello world');
        
    ```
* 按下 ESC 鍵，再輸入 wq! 完成儲存後離開
* 輸入 node app.js 即可看到成果:
    ``` bash
        > Hello world
    ```

    

        

    