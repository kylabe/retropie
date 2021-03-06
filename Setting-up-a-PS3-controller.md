For the most recent version of RetroPie (3.0+)
---
The most recent versions of RetroPie comes with all the packages needed for setting up a PS3 controller, so there is no need to install the required packages separately.

Before booting up our Raspberry Pi, make sure that your Bluetooth adapter is connected to your Raspberry Pi. Also, if you have a playstation game console near by, make sure it is **unplugged**.  The PS3 controller may try to automatically pair with the PS3 game console.  Although a separate powered USB hub is not needed to set up your controller, you would want to get one if you want to overclock your Raspberry Pi.

After your Pi boots up, run the `retropie_setup.sh` script.
```shell
cd RetroPie-Setup/
sudo ./retropie_setup.sh
```
Although it is not required, it is always a good idea to update the setup script by selecting
```shell
U UPDATE RetroPie Setup Script
```

Exit, and run the `retropie_setup.sh` script again. Select:
```shell
SETUP (only if you already have run one of the installations above)
310 Install PS3 controller driver
```
After it finishes compiling, the GUI prompt will ask you to make sure that your Bluetooth dongle is connected. Press enter and connect your PS3 controller.

Once this is done, you should be able to disconnect the controller, and pressing the Playstation button should connect it via Bluetooth.

After installation of PS3 controller driver bluetooth connection of new controllers will be configured automatically if you connect them over usb. 

For older versions of RetroPie
---
For setting up the PS3 Controller we're going to be following This [post](http://booting-rpi.blogspot.ro/2012/08/dualshock-3-and-raspberry-pi.html)

(now oddly i couldn't get to Pair constantly with bluetooth but worked over USB, but for those getting it to work over bluetooth's sake we're going to follow the guide step by step)

First: Besides having a bluetooth adapter :P we're going to install all dependencies required
```shell
sudo apt-get install bluetooth blueman bluez-hcidump checkinstall libusb-dev libbluetooth-dev joystick pkg-config
```
Now that's installed (and a reboot if you plugged in your dongle afterwards) run ```hciconfig``` to make sure it's seeing your dongle, if it has not, a dependency failed to install or your dongle is not supported by RetroPie SD (Raspbian) or the said OS running. you should see an output with information like this:

```shell
pi@raspberrypi ~ $ hciconfig
hci0: Type: BR/EDR Bus: USB
 BD Address: 00:1F:81:00:06:20 ACL MTU: 1021:4 SCO MTU: 180:1
UP RUNNING PSCAN
RX bytes:1260 acl:0 sco:0 events:46 errors:0
TX bytes:452 acl:0 sco:0 commands:45 errors:0
```

Next we're going to pair using this [tool](http://www.pabr.org/sixlinux/sixlinux.en.html)

Downloading and compiling is pretty quick and straight forward:
```shell
wget http://www.pabr.org/sixlinux/sixpair.c
gcc -o sixpair sixpair.c -lusb
```

however sixpair must be run as root, so connect via USB and run ```sudo ./sixpair```.
If successful you should see: 
```shell
Current Bluetooth master: DE:AD:BE:EF:00:00
Setting master bd_addr to: 00:1F:81:00:06:20 
```

now this is where the magic happens

we're going to install an Sixaxis Manager this is what will let us use the controller as an input over bluetooth and USB. (mycase i only got over USB you may vary!)

```shell
wget http://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.1/QtSixA-1.5.1-src.tar.gz
tar xfvz QtSixA-1.5.1-src.tar.gz
```

The source code requires a patch to compile correctly as of right now, so we'll download and apply it
```shell
wget https://bugs.launchpad.net/qtsixa/+bug/1036744/+attachment/3260906/+files/compilation_sid.patch
patch ~/QtSixA-1.5.1/sixad/shared.h < compilation_sid.patch
```

It should now correctly build and install 
```shell
cd QtSixA-1.5.1/sixad
make
sudo mkdir -p /var/lib/sixad/profiles
sudo checkinstall
```

now if we want to make it so per every time we need it on demand: we start the controller daemon like so:
```shell
sudo sixad --start (when it displays its searching, press the PS Button and your golden~!)
```

if we want it at boot time then we use this command:
```shell
sudo update-rc.d sixad defaults
reboot
```

if you have any issues with the controller you can debug it with `sudo jstest /dev/input/js0`

Disconnect Bluetooth Controller
---

To disconnect the controller, hold down the ps3 button for 10 seconds.


***

_this Guide, we have thanks to Donnerstag over at http://booting-rpi.blogspot.ro/ as well as: http://blog.onsw.net/yuta/  (credit must go where it's due :3)_