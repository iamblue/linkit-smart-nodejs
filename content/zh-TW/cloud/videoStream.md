#使用 MCS 來看視訊串流 (草稿)

(本章節功能還尚未 release)

本篇 LinkIt smart 7688 , LinkIt smart 7688 Duo 皆可以適用.

## 準備事項

* 先準備好一條 usb OTG 線
* 準備好您的 web camera ( 本篇範例是使用羅技 C310)
* 將電源線插入PWR, web camera 插入 usb OTG 在插入 7688 上的 HOST 。

## 在 MCS 上要做的事情

* 進去 prototype 詳情頁面，點擊 `Add Data Channel now`:
![](videostream_prototype01.png)
* 創建一個 display 形式的 datahchannel:
![](videostream_prototype02.png)
* Data type 選擇 Video Stream，其他空格按照您的需求輸入，注意這時候打的 data channel id 就是等一下會用到的 `dataChnId` :
![](videostream_prototype03.png)
* 回到 prototype 詳情頁面，點選 `create test device`:
![](videostream_prototype04.png)
* 進去本頁面後，就可以看到 `deviceId`, `deviceKey`:
![](videostream_prototype05.png)


## 在 Device 端要做的事情

* ssh 進去您的 7688:
* 安裝 ffmpeg:

```
opkg update
opkg install ffmpeg
```

* 輸入以下指令: (`deviceId`, `deviceKey`, `dataChnId` 即為上述拿到的代號)
```
ffmpeg -s 176x144 -f video4linux2 -r 30 -i /dev/video0 -f mpeg1video -r 30 -b 800k http://52.76.74.57:8082/{deviceId}/{deviceKey}/{dataChnId}/176/144
```

