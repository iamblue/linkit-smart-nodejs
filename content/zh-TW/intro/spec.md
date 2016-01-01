## 前言

聯發科在 2015/12/1 當天發布兩塊 LinkIt smart 系列的版子，分別為 7688 及 7688 Duo。


## 架構圖：

![](7688&Duo.png)

這是簡單架構圖表示 7688 與 7688 Duo，我們可以看到兩塊版子都使用 MT7688 晶片。 7688 Duo 比 7688 多一顆 Arduino 晶片 (32U4)，簡單來說，擁有 Duo 人可以多出使用 Arduino sensor 的玩法。 

## 開發板規格

這次在設計兩塊 7688 開發板規格時，有針對 Memory 和 flash 去做適合高階語言的玩家調查，這樣的規格下 npm install 較不會發生 ran out of memory 以及空間不夠 (連 Node.js 都裝不起來) 的問題。以下是規格：
![](7688boardspec.png)
![](7688Duoboardspec.png)

## 關於 MT7688

以下是 MT7688 這塊晶片的規格，我們可以知道他屬於 ap router 的晶片產品，屬於 MPU 等級的晶片。

![](7688spec.png)