# pi-zzolo

Configs, scripts, and docs for Raspberry Pi.  Assuming Raspbian.

## Initial setup and configuration

* Download Raspbian image from [RaspberryPi.org](http://www.raspberrypi.org/downloads).
* (on Mac) Use [Pi Filler](http://ivanx.com/raspberrypi/) to burn to SD card.
* Configure system.  On initial launch, the system configuration will show, but this can be access later with: `sudo raspi-config`
    * Expand filesystem 
    * Change user password (default user is `pi`)
    * Internationalization options
    * Advanced options: Enable SPI
    * Advanced options: Change hostname
* Connect to internet if not already.
* Run `sudo rpi-update` to update firmware.
* Update packages: `sudo apt-get update && sudo apt-get upgrade`
* (on Mac) Make an image of all the updated stuff with [Pi Cobler](http://ivanx.com/raspberrypi/).

## Peripherals

### Wi-Pi

The drivers and WPA tools (wpasupplicant) should already be installed on Raspbian.  I used [this tutorial](http://www.raspberrypi-tutorials.co.uk/set-raspberry-pi-wireless-network/) to get things working correctly.

Make sure ```/etc/network/interfaces``` has a block like the following:

    auto wlan0
    allow-hotplug wlan0
    iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

Make sure ```/etc/wpa_supplicant/wpa_supplicant.conf``` has a block like the following:

    network={
      ssid="SSID_HERE"
      psk="PASS_HERE"
      proto=RSN
      key_mgmt=WPA-PSK
      pairwise=CCMP TKIP
      group=CCMP TKIP
    }

Restart with `sudo /etc/init.d/networking restart`
