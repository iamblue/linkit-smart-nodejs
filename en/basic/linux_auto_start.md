## How to make your Node.js app start automatically on LinkIt Smart 7688 booting?

### Aim

In this section, we are going to use some basic linux commands to make developer's Node.js app start automatically on LinkIt Smart 7688.

### Prerequisites

* Your awesome Node.js App

### Process

* Make sure your board is connected properly.
* ssh into it.
* Edit `/etc/rc.local`:

```
    vim /etc/rc.local
```

* Refer to the content below and make `/etc/rc.local` into your app's path:

```
#!/bin/sh -e

node /root/app/app.js

exit 0
```

* After file saved, setup `/etc/rc.local` permissions:

```
chmod 777 /etc/rc.local

```
* Reboot and you will see the results! Bravo!
