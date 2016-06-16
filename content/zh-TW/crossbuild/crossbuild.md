## 交叉編譯 node.js 原生模組 

### 說明

此章節介紹如何交叉編譯那些需要重新建置的 node.js 原生模組。

附註： 當你在安裝一些需要 rebuild 的 node 模組時，可能會遭遇一些困難，閱讀這個章節或許可以幫上忙。

## 環境準備

### 準備 host PC
* 作業系統: Ubuntu 14.04 LTS x86_64
* Node 版本: 0.12.7 (你可使用 **n** 或 **nvm** 版本管理員來切換你的 node 版本，以下範例使用 **n**)

    ``` bash
    $ sudo n 0.12.7
    ```

* Npm 版本: 2.11.3

    ``` bash
    $ sudo npm install -g npm@2.11.3
    ```

* 在 Ubuntu 上安裝所需的套件

    ``` bash
    $ sudo apt-get install subversion build-essential gcc-multilib g++-multilib
    ```

* Clone [mt7688-cross](https://github.com/simenkid/mt7688-cross) 專案至你的 Ubuntu。(如果你沒有 git，可以直接下載此專案的 zip 壓縮檔)  


    ``` bash
    $ git clone https://github.com/simenkid/mt7688-cross.git
    ```

* 進入工作目錄 `mt7688-cross/`，執行指令稿 `./create_env.sh` 以在工作目錄中創建交叉編譯環境。這個步驟可能需耗時 20 分鐘左右，請稍微耐心等候。  

    ``` bash
    $ cd mt7688-cross
    ~/mt7688-cross $ 
    ~/mt7688-cross $ ./create_env.sh
    ```

    * 附註： 一旦此步驟將建置環境準備好之後，以後每次你想交叉編譯 node 原生模組，就進來此工作目錄 `mt7688-cross/` 中執行 `npm_install.sh` 來安裝模組即可。你不需要重新執行 `./create_env.sh`。  

### 將原生模組安裝至 Linkit Smart 7688 的步驟  

* 首先，在工作目錄中執行 `npm_install.sh` 指令稿來安裝你想建置的原生模組。  

    ``` bash
    ~/mt7688-cross $ ./npm_install.sh foo-module
    ```

    * or install a specified version  

    ``` bash
    ~/mt7688-cross $ ./npm_install.sh foo-module@version
    ```

    * Let's take installation of `serialport` module as an example:  

    ``` bash
    ~/mt7688-cross $ ./npm_install.sh serialport
    ```
![](crossbuild_serialport.jpg)

* 交叉編譯完成的模組，會以壓縮檔的形式存放於 `mt7688-cross/node_modules_mips` 目錄底下。  

    ``` bash
    ~/mt7688-cross $ cd node_modules_mips
    ~/mt7688-cross/node_modules_mips $ ls
    ```

* 將模組壓縮檔上傳至 Linkit Smart 7688。  
    
    ``` bash
    ~/mt7688-cross/node_modules_mips $ scp foo-module-x.y.z.tar.gz root@192.168.0.109:/root/app
    ```
![](crossbuild_scp_to_7688.jpg)

    * 附註： 請將 `192.168.0.109` 換成你的 Linkit Smart 7688 實際使用的 IP。請將 `/root/app` 更改為你想上傳過去的遠端目錄路徑。  

* ssh 進入 Linkit Smart 7688。
    
* 進入剛剛你所上傳的目錄，將模組壓縮檔解壓至同目錄底下的 `node_modules/` 資料夾。  

    ``` bash 
    > cd app
    ~/app > tar -xvf foo-module-x.y.z.tar.gz -C node_modules/
    ```
![](crossbuild_uncompress.jpg)

* 現在，就跟使用一般的模組一樣，你可以開始撰寫一支 `app.js` 來測試你所交叉編譯完的 node 原生模組了。

        
