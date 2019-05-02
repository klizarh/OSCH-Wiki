# OneWire Sensors - DS18B20 Temperature Sensors

## Description
OneWire is a special protocol used by numerous devices.  The NerdFarm is using the OneWire temperature probes (DS18B20), which are cheap and waterproof.
Data is not read directly, but the underlying modprobe application reads the sensors and writes data to files.  Our programs read the files.

## Setup
OneWire used modprobe (part of the standard intallation), but requires some custom file modification to get it to work.  You need to edit /boot/config.txt (sudo leafpad /boot/config.txt), and add the following line to the end of the file:

dtoverlay-w1-gpio-pullup

## Technical Reference
* [AdaFruit](https://www.adafruit.com/product/381)