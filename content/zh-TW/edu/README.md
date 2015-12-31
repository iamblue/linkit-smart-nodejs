## 教育方案

我們觀察 Maker 教育上的分成兩個族群，為會使用 Linux 以及不會使用 Linux 族群，剛好 LinkIt smart 7688 與 LinkIt smart 7688 Duo 分別代表這兩個族群。

 國中小學生因沒有基礎 Linux 知識，加上 Arduino community 已有各種拖拉式 GUI 介面 open source 軟體 (例如 Scratch) 因此這族群的以使用 Arduino 為主要開發，因此在教育上我們建議:

* 國中小學： LinkIt smart 7688 Duo
* 高中. 大學： LinkIt smart 7688 or LinkIt smart 7688 Duo

本章節來講若您是屬於想提供 『國中小學』的教材者，務必要提供的事情

## LinkIt smart 7688 Duo 把 Yunbridge 開啟

在多數的物聯網專案都需要 wifi 需求，而 Duo 上的 7688 可以提供 wifi 給沒有 wifi 的 Arduino chip 使用。但是 Duo 預設的運算上以 MPU 為主 MCU (Arduino) 為輔，因此需要去把 Yunbridge 做開啟的動作：

* 首先，先進到 WebUI 把 Duo 設定成 station mode 到外網。
* 透過 ssh 進去 LinkIt smart 7688 Duo:
```
    ssh root@mylinkit.local
```
* 把 yunbridge 開啟:
```
    uci set yunbridge.config.disabled=0
```
* 儲存下：
```
    uci commit
```
* 重新開機:
```
    reboot
```

## 在Arduino 端用 HttpClient 確定 bridge 已通。 

* 打開你的 Arduino IDE
* File -> example -> Bridge -> HttpClient
* 把這個範例燒錄進去
* 打開 Arduino 監控視窗，看到這畫面即代表成功。
* ![](httpclient.png)

## 完成以上教材準備後，就可以讓學生只專心在 Arduino IDE 上開發物聯網專案。
