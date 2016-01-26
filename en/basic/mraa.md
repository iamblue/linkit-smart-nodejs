## Use mraa kit to control GPIO 

### Aim

In this section, we are going to use `mraa` to control GPIO.

Note: The LED lights to be controlled in this example is the same as wifi one on the board.

## Controlling LED (outputting GPIO messages)

### Steps
* ssh into Linkit Smart 7688.
* Generate a project.

    ``` bash
    > mkdir app
    ```

* Use npm to initialize your project.
    
    ``` bash
    > npm init
    ```
    
* Generate an app.’s file.
    
    ``` bash 
    > vim app.js
    ```
    
* Enter the content in `app.js`.
    
``` js
var m = require('mraa');
var ledState = true;
var myLed = new m.Gpio(44);

myLed.dir(m.DIR_OUT);

function periodicActivity() {
    myLed.write(ledState ? 1 : 0);
    ledState = !ledState;
    setTimeout(periodicActivity, 1000);
}
periodicActivity();
```
    
* Then, we can see the results!

![demo](http://iamblue.gitbooks.io/linkit-smart-nodejs/content/images/blink.gif)

        

    