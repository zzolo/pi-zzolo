# pi-zzolo

Configs, scripts, and docs for Raspberry Pi.  Assuming Raspbian.

## Initial setup and configuration

* Download Raspbian image from [RaspberryPi.org](http://www.raspberrypi.org/downloads).
* (on Mac) Use [Pi Filler](http://ivanx.com/raspberrypi/) to burn to SD card.
* Configure system.  On initial launch, the system configuration will show, but this can be access later with: `sudo raspi-config`
    * Expand filesystem 
    * Change user password (default user is `pi` and password is `raspberry`)
    * Internationalization options
    * Advanced options: Enable SPI
    * Advanced options: Change hostname
* Connect to internet if not already.
* Run `sudo rpi-update` to update firmware.
* Update packages: `sudo apt-get update && sudo apt-get upgrade`
* (on Mac) Make an image of all the updated stuff with [Pi Cobler](http://ivanx.com/raspberrypi/).

## Peripherals

### Wi-Pi

1. [Reference](http://www.element14.com/community/servlet/JiveServlet/previewBody/49107-102-1-257014/Wi_Pi.User_Manual.pdf) for the Wi-Pi
1. Edit `/etc/network/interfaces`:

```
auto lo
iface lo inet loopback
iface eth0 inet dhcp
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
wpa-ssid YOUR SSID HERE
wpa-psk YOUR PASSWORD HERE
```
1. Restart with `sudo /etc/init.d/networking restart`
