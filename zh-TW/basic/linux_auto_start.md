## 如何讓 LinkIt smart 7688 開機時自動啟動您的 Nodejs App ?

### 說明

這個章節我們來透過 linux 的基本指令讓 LinkIt smart 7688 開機時自動啟動開發者的 Nodejs App.

### 須先準備

* 你的 awesome Nodejs App

### 流程

* 確定跟你的版子已連線
* ssh 進去
* 編輯 /etc/rc.local:

```
    vim /etc/rc.local
```

* 參考這內容把 `/etc/rc.local` 編輯程你想要執行的 app 路徑:

```
#!/bin/sh -e

node /root/app/app.js

exit 0
```

* 存檔後，設定 `/etc/rc.local` 權限:

```
chmod 777 /etc/rc.local

```
* 重新開機後就可以看到結果囉！
