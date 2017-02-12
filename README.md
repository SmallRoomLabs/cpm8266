# cpm8266

## CP/M 2.2 for Z80 emulator running on ESP8266

## Please note that this is still early work-in-progress

### What

This is my attempt to run CP/M 2.2 for Z80 softwares on an ESP8266.
The CP/M machine have 64K RAM, 8 Floppy drives @ 250KB each and a serial
port running initally at 19200 baud as a comsole device.

The ESP8266 only have 96KB of Data RAM and even when runnig the "NO
OS-firmware from Expressif the free HEAP, after the WIFI & TCP/IP stacks are
loaded, is less than 48KB which was my minimum goal for CP/M RAM.

Luckily the Cnlohr NoSdk2866 project came can solve the RAM issue. Using the
NoSdk there are more than 80KB of free HEAP which is more than enough for
the 64KB RAM in the Emulator.  This unfortunately comes with a cost -
namlely no WIFI.  Not a showstopper for me, but it would have been nice to
be able to just Telnet into the CP/M machine to connect to the emulated
terminal. (Some day I'll run this on the ESP32 that have plenty of free RAM
when whith the FreeRtos and WIFI running.)

### Installing, Compiling and Running

You will need ESP-Open-SDK installed. If you don't already have it you can
get it at https://github.com/pfalcon/esp-open-sdk. Just follow the
instructions for there and br prepared for a lengthy (but automates)
process.

Then clone the code for this project with:
```git clone git@github.com:SmallRoomLabs/cpm8266.git```

Unless you have the same serial port for the ESP and the same location of
the OpenSDK installation as me you either have to change the Makefile or
setup two environment variables:
```
export ESP8266SDK=/opt/esp-open-sdk
export ESPPORT=/dev/ttyUSB0
```
Then just a `make clean && make && make flash` to compile and upload to the
ESP.




### Acknowledgements and thanks
I'm standing on the shoulders of a lot of really smart people here. Without
their contributions I wouldn't even know where to start.

Paul Sokolovsky @pfalcon made the Esp-Open-SDK installer/setup
https://github.com/pfalcon

Lin Ke-Fong @anotherlin made the Z80 Emulator
https://github.com/anotherlin

Charles Lohr @CNLohr created the NoSDK for the ESP8266
https://github.com/cnlohr

Tim Olmstead (RIP) for managing to free the CP/M sources from the owners
http://www.cpm.z80.de/ 