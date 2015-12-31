## How to use video streaming 

### Aim

In this section, we are going to create video streaming through mjpg-streamer.

### Prerequisites
* webcam: uvc specification is recommended. In this example, Logitech C310 camera is taken.


### Installation
* Make sure mjpg-streamer is installed on LinkIt Smart 7688.

### Work Principle
* Basically, this would be working if `mjpg-streamer` is installed.
* Type the following command in the command line:
``` bash
> mjpg_streamer -i "input_uvc.so -d /dev/video0 -r 640x480 -f 25" -o "output_http.so -p 8080 -w /www/webcam" &
```
* Open `http://mylinkit.local:8080` in your browser. If you see the video, it works properly.
