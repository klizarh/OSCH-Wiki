## Architecture
Software is in two parts:
* Code running locally on the MVP's Raspberry Pi
* User Interface (UI) code running on the cloud server

The MVP code currently consists of three main parts:
* Controller (currently the Linux CRON process): control the timing of events
* Scripts (/home/pi/MVP/scripts): these package the Python code for group operations, and provide separation between the controller and functions.
* Code (/home/pi/MVP/python): most actions are executed through Python code files.  This code represents sensors, controllers, utilities (data handling,logging, ...) and reporting.

## Releases
* V1
* V2.1
* V3

## [Coding Standards](https://github.com/futureag/blog/wiki/Software_Standards)

## [Data_Model](https://github.com/futureag/blog/wiki/Data_Model)