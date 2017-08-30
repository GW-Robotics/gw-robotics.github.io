+++
title = "Testing Arduino-Raspberry Pi Serial Comms"
date = "2016-10-26T02:15:43"
tags = ["setup"]
categories = ["control-systems"]
+++
Tonight, Nam went through a [tutorial](http://www.instructables.com/id/Raspberry-Pi-Arduino-Serial-Communication/) on communicating via a USB cable between an Arduino and a Raspberry Pi. Here are a few things to note:
- The tutorial did not mention the need to download PySerial. This was done via pip.
- The Arduino sketch was compiled via a computer, and then the Arduino was connected to the Raspberry Pi.
- The Raspberry Pi python program was written using Nano.

The test program was successful. The next logical step is to work on creating a Python Module and an Arduino Sketch to control the Arduino's Digital I/O through Serial.
