# EsPiFF
An ESP32 in the Raspberry Pi form factor

## Meet the EsPiFF - The ESP32 in the Raspberry Pi 4 form factor

![The EsPiFF](/images/espiff_angehoben.jpg)

For applications, where the Raspberry Pi 4 is not robust enough, or take too much power, you can consider the EsPiFF as an option.
The EsPiFF (V2) brings
 - ESP32-WROVER with dual core, 8MB PSRAM, 16 MB Flash
 - Ethernet wired and Wifi
 - SD-card for data storage
 - up to 3 UARTs
 - an USB-C connector for power supply up to 5V, 3A
 - a Rasperry Pi header with 40 pin, compatible to all Raspberry Pi HATs

The EsPiFF V3 will bring the following 
 - an RP2040 IO-processor additional to the ESP32
 - 2kByte FRAM for high-speed permanent storage
 - RTC Realtime clock
 - USB-A connector for USB-Host

We desided, to build an alternative to the Raspberry Pi for our projects and products. 
As many other as well, we was using the Raspberry Pi in our products, adding electronic payment to existing vending machines and coffee machines, in RFID solutions to read RFID tags in laundry, and other application. While it was easy to get a solution up and running in a short time, over time we got a log of trouble resulting for using the Pi. 

A key problem is the Pi's design, to relay on an SD-card. The SD-cards are made for digital cameras, to write on them a few times. A Linux system like the Pi on the other hand, is writing permanent its log files, and swap partition, to the SD-card. As a result, after a short time the SD-card break and the application crash. High-end industrial SD-card hold longer, but finally still break. 

The PI Operating system is also great for fast bring-up of a solution, but its more and more focused on media streaming then real-time tasks. 
So we made the decision, to build a replacement, what is focused on high-reliability, but still enable the use of Raspberry Pi universum of add-ons, like HATs and enclosures. We choose the ESP32 dual core, 2x240MHz WROVER module with 8MB PSRAM and 16MB Flash. The EsPiFF, the **Es**p32 in Raspberry **Pi** **F**orm **F**actor was born.

## History
### Version 1
The first version of the EsPiFF was born in a time, where all Ethernet Phy chips was unavailable. Our first prototype used a Waveshare LAN8720 module. Interestingly, even no LAN8720 chips could be bought anywhere, but the modules was still available. Because the Waveshare module did not route the enable signal to the pin header, but left one pin unconnected on the pin header, we had to solder a wire from the oscillator to that unused pin on the header. After these, the board run well, and do so till now. We added 4 high side switches, and digital inputs to operate 4 door locks. These are the 4 white connectors opposite the RJ45 connectors. The Version 1 had the WROOM module of the ESP32.  

We ported the PostgreSQL client libray to the ESP32, what worked very well, even with the limited RAM and Flash. Not only SELECT, INSERT and UPDATE work, but also the brilliant PostgreSQL feature NOTIFY. As a result, the EsPiFF dont need to poll the PostgreSQL server, but get notified instead. We could define a trigger in PostgreSQL, and notify other EsPiFF board. Thats very cool.

### Version 2
After the LAN8720 chips got available again, we decided to make a new board revision. These are the current boards. We used the ESP32-WROVER module, for additional 8MB PSRAM and 16MB Flash. We also added an SD-card. Unfortunately, we used the wrong pinout, make it very difficult to change the SD-card. An other issue was a missing pull-up resistor on the LAN8720. 
We changed the USB connector to a Type-C connector, and configured it so, that 5V and up to 3A can be taken. Thats a big improvement, raising the available power from 0.5W to 15W. We removed the 4 door lock connectors, and put them on a HAT. 
Since version 1 we have a "Chafon-Connector", next to the USB connector. It is to connect the Chafon RFID Rain(UHF) modules. Additional, we replaced the UART pin headers with more robust JST connectors, left and right of the SD-card. 

We could also compile and flash the Apache Nuttx operating system on the new board. A growing number of people are using ESP32-WROVER boards together with Nuttx as OS. This offers an somehow easy path of porting Linux and Raspberry Pi software on ESP32+Nuttx. 

### Version 3
This is the planned final version. Additional to the fix of the 2 known issues, we plan the following:
 - adding a I2C-RTC: a real-time clock will be needed for planned PLC usage.
 - adding a 2kBy FRAM: again for PLC application, a fast and non-volatile memory is needed. It offers near infinity write/read cycles compared to flash.
 - replace the WROVER module with a version with u.FL/IPEX connector. This enables an external antenna.
 - adding a RP2040 co-processor. The ESP32 just not have enough pins free, to operate all the pins on the Raspberry Pi 40pin header. The last solution with the I2C port expander is too slow and unflexible. The much more powerfull RP2040 will solve these problem. It also offers an USB host port!

After the EsPiFF is not mature enough, we we are preparing a campaign at Crowd Supply. After the Pre-launch is available, we will update the info here. Hope you support us on our Crowd Supply campaign!

Team MDC
