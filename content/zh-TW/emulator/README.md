## LinkIt smart 7688 模擬器

### 前言

LinkIt smart 7688 本身只有 32mb flash 以及 128 mb Memory, 對於想在版子上面做一些較耗資源的開發過程需要的東西，例如 cross compile 是非常痛苦的（因為這時候需要較多的 Memory 空間）因此在社群上有大神 (Fred) 針對 LinkIt smart 7688 的 Image 出一套 qemu 上的模擬器， 我們可以在這個模擬器上面模擬更多記憶體和硬碟空間，去幫助我們克服這些事情。

### 相關連結

https://github.com/cfsghost/makerboard

### 如何使用

* 首先，先起一台 Ubuntu server (after 14.04 version)
* 在這台 Server 安裝好 Node.js 4 環境
* 安裝 Ubuntu 對應套件:
```
sudo apt-get install qemu-user-static squashfs-tools
```
* 安裝 makerboard: `npm install makerboard -g`
* 創建 emulator: `makerboard create my7688`
* 跑出模擬器: `makerboard run my7688`

注意：若您發現有這個字樣`/bin/sh: Invalid ELF image for this architecture` 因為目前的 Ubuntu qemu core 的版本有 bug，這時要做一件事情：

* 下載 qemu-core-static for ubuntu 14.04

```
wget https://s3-ap-southeast-1.amazonaws.com/mtk.linkit/qemu-core-static
```

* 複製進剛剛 makerboard 創建好的 my7688/usr/bin:

```
cp qemu-core-static ./my7688/usr/bin/
```

最後再 run 一次模擬器:

```
makerboard run my7688
```

看到這樣的畫面即代表進去 LinkIt smart 7688 模擬器囉！

![](7688emulator.png)


