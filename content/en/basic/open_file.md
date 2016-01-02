## Open files on microSD

### Aim

In this section, we are going to read files in the microSD within LinkIt Smart 7688.

### Steps

* Insert a microSD into LinkIt Smart 7688.
* ssh into your LinkIt smart 7688.
* Generate a folder named ‘app'.
    ```sh
        > mkdir app
    ```
* Generate `app.js`. 
    ```sh
        > vim app.js
    ```
* Press `i` and edit `app.js`:

``` js
var fs = require('fs');
// **** Remarks ****
// 1. The following SD-P1 stands for read first partitions in SD card.
// 2. On Linkit Smart, all files will be found in /Media folder no matter whether you pick usb host or SD card.
fs.readdir('/Media/SD-P1', function (err, data) {
    if (err) throw err;
    console.log(data);
});
        
```
    
* Press `ESC`, then enter `wq!` to save and leave.
* Enter `node app.js`, and the results can be seen! 


    

        

    