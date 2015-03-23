# Configuring Wifi

First check to see if your wifi dongle is [compatible](http://elinux.org/RPi_USB_Wi-Fi_Adapters):

There are two main methods to configure Wifi.

## Method 1

`sudo nano /etc/network/interfaces`

Then change the file to look like this:

```shell
sudo nano /etc/network/interfaces

Configuration File:
auto lo
iface lo inet loopback
iface eth0 inet dhcp
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
   wpa-ssid "Your Wireless Network Name"
   wpa-psk "Your Wireless Network Password"
```
you can also add "wireless-power off" at the end (without quotations) if you have issues with your wifi dongle turning off and on a lot and not being able to maintain a connection.

## Method 2

**Taken from the Raspberry Pi Foundation [here](http://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md):**

This method is suitable if you do not have access to the graphical user interface normally used to set up WiFi on the Raspberry Pi. It is especailly suited for use with a serial console cable if you don't have access to a screen or wired Ethernet network. Also note that no additional software is required; everything you need is already included on the Raspberry Pi.

### GETTING WIFI NETWORK DETAILS

To scan for WiFi networks, use the command `sudo iwlist wlan0` scan. This will list all available WiFi networks along with other useful information. Look out for:

1. `ESSID:"testing"`. This is the name of the WiFi network.

2. `IE: IEEE 802.11i/WPA2 Version 1`. This is the authentication used; in this case it is WPA2, the newer and more secure wireless standard which replaces WPA1. This guide should work for WPA or WPA2, but may not work for WPA2 enterprise; for WEP hex keys see the last example [here](http://netbsd.gw.com/cgi-bin/man-cgi?wpa_supplicant.conf+5+NetBSD-current). 
You will also need the password for the WiFi network. For most home routers this is located on a sticker on the back of the router. The ESSID (ssid) for the network in this case is `testing` and the password (psk) `testingPassword`.

### ADDING THE NETWORK DETAILS TO THE RASPBERRY PI

Open the `wpa-supplicant` configuration file in nano:

`sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`

Go to the bottom of the file and add the following:
```shell
network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
}
```
In the case of the example network, we would enter:

```shell
network={
    ssid="testing"
    psk="testingPassword"
}
```
Now save the file by pressing **ctrl+x** then **y**, then finally press **enter**.

At this point,` wpa-supplicant` will normally notice a change has occurred within a few seconds, and it will try and connect to the network. If it does not, either manually restart the interface with `sudo ifdown wlan0` and `sudo ifup wlan0`, or reboot your Raspberry Pi with `sudo reboot`.

You can verify if it has successfully connected using `ifconfig wlan0`. If the `inet addr` field has an address beside it, the Pi has connected to the network. If not, check your password and ESSID are correct.