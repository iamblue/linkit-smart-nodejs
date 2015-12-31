## Preface

Mediatek Inc. released two LinkIt smart series boards on 2015/12/1 - 7688 and 7688 Duo, respectively.


## Framework Diagram

![](https://iamblue.gitbooks.io/linkit-smart-nodejs/content/content/zh-TW/intro/7688&Duo.png)

This simple framework diagram shows the 7688 and 7688 Duo, as we can see, both these two boards use MT7688 chip. 7688 Duo has one more Arduino chip (32U4) than 7688. Simply speaking, users with 7688 Duo can have more options to play with Arduino sensors.


## Development Board Specification

During defining the specifications for these two 7688 development boards, the memory and flash suitable for high level language players have been surveyed. Under this specification, the problems encountered in the npm install could be nearly avoided, for example, ran out of memory, or storage space shortage (even can not install Node.js). Here is the specification:
![](7688boardspec.png)
![](7688Duoboardspec.png)

## 關於 MT7688

以下是 MT7688 這塊晶片的規格，我們可以知道他屬於 ap router 的晶片產品，屬於 MPU 等級的晶片。

![](7688spec.png)