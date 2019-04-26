# Shroom Farm
The Shroom Farm is a mushroom fruiting box.  It uses most of the same code as the NerdFarm,  with a few additions and changes.  Since the CO2 sesor (SCD30) was introduced, we thought we should put it to a meaningful use; the sensor is tied via a controller to a small fan, to regulate the CO2 levels in the box.
![Shroom Farm](https://github.com/futureag/blog/blob/master/static/images/ShroomFarm.jpg)

## Basic Design
The Shroom Farm replaces the NerdFarm enclosure with a smaller plant tray and plastic dome.  Like the NerdFarm there is a Raspberry Pi brain, one sensor (SCD30), a relay, two fans and a humidifier.  There are no lights, and mushrooms need little light for fruiting.

## Parts List
* Raspberry Pi
* Two bay relay
* USB Camera
* SCD30 CO2 sensor
* 2 Raspberry Pi 5v fans
* USB humidifier
* Jumper wires
* Zip ties
* 2 Wegos
* Scrap wire (to hang a fan)
* A scrap of foamboard to mount the Raspberry, relay and camera
* Double-sided tape to attach the foamboard to the dome.

## Build
If you have built the NerdFarm, you should have enough skills to figure out the Shroom Farm. 

Both relays are wired to 'normal off', and the power is wired to one of the Raspberry's 5v pins (jumper the power between the two relay power inputs).
There are not enough 5v pins on the Raspberry for all the power needs, so get a couple of Wegos and use them to create a multi-outlet (or use your soldering skills with some jumper wires).
You will need to cut the USB end off of the humidifier and solder on a couple of jumper.  There are only two wires, so it shouldn't be too difficult to figure out.
One relay powers the humidifier, the other powers the exhaust fan (mounted on the top-middle of the dome to push IN fresh air.
The other fan is hung from a wire and always on (like the NerdFarm).

## [[Growing Mushrooms | Growing_Mushrooms]]