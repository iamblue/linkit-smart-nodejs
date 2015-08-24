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
* 安裝


    

        

    