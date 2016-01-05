#使用 MCS 來看視訊串流

本篇 LinkIt smart 7688 , LinkIt smart 7688 Duo 皆可以適用.
## 在 MCS 上要做的事情

* 進去 prototype 詳情頁面，點擊 `Add Data Channel now`:
![](videostream_prototype01.png)
* 創建一個 display 形式的 datahchannel:
![](videostream_prototype02.png)
* Data type 選擇 Video Stream，其他空格按照您的需求輸入，注意這時候打的 data channel id 就是等一下會用到的 `dataChnId` :
![](videostream_prototype03.png)
* 回到 prototype 詳情頁面，點選 `create test device`:
![](videostream_prototype04.png)

![](videostream_prototype05.png)


## 在 Device 端要做的事情

* ssh 進去您的 7688:
* ffmpeg -s 176x144 -f video4linux2 -r 30 -i /dev/video0 -f mpeg1video -r 30 -b 800k http://52.76.74.57:8082/{deviceId}/{deviceKey}/{dataChnId}/{deviceKey}/{width}/{height}
