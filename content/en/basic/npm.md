## Installation Node.js suite on LinkIt smart 7688

### Aim

This section explains how to install the Node.js suite you need on LinkIt smart 7688.

If you encounter some problems on the installing Node.js suite, you can also find your answer in the following `Troubleshooting` list.

### Steps

* Make sure the board is connected with your computer correctly.
* ssh into your board.
* Go into your Node.js project folder.
* For example, I want to install express package, enter:
    
    ```
        npm install express
    ```
* If you see the following screen, it is all done. Cheers!

PS. If your package is to be installed on the Node.js global environment, enter:
``` 
    npm install express -g
```

### Troubleshooting

#### Q. `npm install` waits too long or shows connection timed out
A. For connection time out issue, please check your network first. For `npm install` time too long, please check if sort of `node-gyp`... or similar strings shows up during the npm install process. If there is, that is because cross compile problem. MPU on LinkIt Smart 7688 need longer running time since it is not as powerful as your desktop or notebook computer. 

It is recommended if such situation encountered, we need to use openWRT toolchain to build the ipk file, and then install the ipk with `opkg install` on Smart 7688. Related `Makefile` for building `node-gyp` package, please refer to(https://github.com/openwrt/packages/tree/master/lang/node-serialport) 
    
        

    