## FOTA

### 如何從 Arduino IDE build 出 hex 檔 for Arduino chip?




### 在 LinkIt smart 7688 所需要的準備。
* ssh 進去 LinkIt smart 7688 
* create new folder 
* npm init
* npm install mcsjs
* copy this code:
* 若您希望每次開機時啟動這段 code 

### 如何利用 MCSjs 利用 FOTA 更新 Arduino?

* 首先，先進去你的 Protoype:
![](fota01.png)
* 點選firmare
![](fota02.png)
* 點選 Add firmware，打入以下資料( File upload 就是上傳從Arduino IDE 所輸出的 .hex 檔):
![](fota03.png)
* 進到第二步驟後，按下`Next`:
![](fota04.png)
* 完成後，點選 Done:
![](fota05.png)
* 若您尚未創建 Test device，請記得在頁面上點選` Create test device`
* 進去您產生好的 Test device 頁面
* 點選 firmware :
![](fota06.png)
* 若您的 Device 已在線上，這個 Push 按鈕就會變成藍色，點擊後就可以進行 FOTA 推送新的 firmware 給 7688 囉。
