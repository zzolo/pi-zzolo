# pi-zzolo

Configs, scripts, and docs for Raspberry Pi.

# About

* OS: Raspbian

# Updates/Upgrades

## Firmware upgrade

* Using [rpi-update](https://github.com/Hexxeh/rpi-update/).

## Raspbian

* ```apt-get dist-upgrade``` installs gnome.  Don't think this is the preferred way to upgrade.

# Configuration

* Use the following to configure raspberry pi: ```sudo raspi-config```

# Packages

Manually installed packages:

* ```git-core```

# Peripherals

## Wi-Pi

The drivers and WPA tools (wpasupplicant) should already be installed on Raspbian.  I used [this tutorial](http://www.raspberrypi-tutorials.co.uk/set-raspberry-pi-wireless-network/) to get things working correctly.

Make sure ```/etc/network/interfaces``` has a block like the following:

    auto wlan0
    allow-hotplug wlan0
    iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

Make sure ```/etc/wpa_supplicant/wpa_supplicant.conf``` has a block like the following:

    network={
      ssid="SSID_HERE"
      proto=RSN
      key_mgmt=WPA-PSK
      pairwise=CCMP TKIP
      group=CCMP TKIP
      psk="PASS_HERE"
    }

