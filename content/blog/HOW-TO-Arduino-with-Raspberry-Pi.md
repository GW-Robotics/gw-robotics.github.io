+++
title = "HOW-TO: Arduino with Raspberry Pi"
date = "2016-10-29T02:04:04"
tags = ["how-to"]
categories = ["control-systems"]
banner = "img/banners/banner-arduino.jpg"
+++
The 2017 robot will be interacting between the Arduino (for sensor reading and PWM output) and the Raspberry Pi through a Python module called [Nanpy](http://nanpy.github.io/). The purpose of this how-to is for basic setup and usage that may not be completely obvious from Nanpy's official documentation. We will be using repositories from the GW Robotics organisation as a way to standardise everyone's code bases.

## Arduino Setup
**Please note, this is only necessary if the Arduino does not already have the Nanpy firmware compiled on it.**

First, you will need to clone the [Nanpy Firmware repository](https://github.com/GW-Robotics/nanpy-firmware) from Github. Then you will go into the repository and run the configure.sh script. The commands is as follows:

```shell
git clone https://github.com/GW-Robotics/nanpy-firmware.git
cd nanpy-firmware
./configure.sh
```

This will create a cfg.h file that you can edit. For an initial setup, I changed the value of USE_Servo to 1, as this will more than likely be used on the robot. The others can be changed and recompiled to the Arduino as they are needed.

After that is completed, copy the /Nanpy/ directory from the repository into your Arduino sketchbook. In most cases, that is the /Arduino/ folder in your Documents directory. After that is done, open "Nanpy.ino" in your Arduino IDE. We are using an Arduino Mega 2560, so set your board to that. Set your port to whatever COM port the Arduino board is found. Verify and compile, and you should be all set to go.

## Raspberry Pi Setup
**Please note, you should already have Python and Python-Pip installed on your computer.**

This honestly is much easier than setting up the Arduino. All you have to do is run the following command to install the Python module and you are ready to program:

```shell
sudo pip install nanpy
```

The only thing that could go wrong is if your Python installation did not come with Pyserial. You can check your installed modules using this command:

```shell
pip list
```

If that is the case, run this command:

```shell
sudo pip install pyserial
```

## Usage
I am going to just paste in the test program I ran to make sure things are working. For the most part, all Arduino functions will work with Nanpy. This makes the usage explanation really easy, though I will note a few interesting points to remember.

```python

from nanpy import ArduinoApi, SerialManager
from time import sleep

print "Establishing connections..."
connection = SerialManager(device = '/dev/ttyACM0')
a = ArduinoApi(connection = connection)

print "Settting up output pin..."
a.pinMode(13, a.OUTPUT)

print "Loop time!"
while True:
      a.digitalWrite(13, a.HIGH)
      sleep(0.5)
      a.digitalWrite(13, a.LOW)
      sleep(0.5)
				
```

The first important thing to note is the imports. You will need to at the very least import ArduinoApi and SerialManager from Nanpy. These are so that Python can run Arduino functions and to connect to the Arduino, respectively. The sleep function should also be imported, as it is used rather than the Arduino delay() function.

The next important thing to note is that all the Arduino loop code is in an infinite while-loop. This is because Nanpy does not provide a loop() function, but this does the same thing. In the future, we need to figure out how to loop that separate from the rest of the code.