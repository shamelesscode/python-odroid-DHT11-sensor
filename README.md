# Python Library for DHT11 Sensor on ODROID Platform

This simple class, written purely in Python, makes it possible to interface with a DHT11 temperature and humidity sensor from ODROID platorms running Ubuntu using ODROID's Ubuntu PPA provided [odroid-wiringpi](https://wiki.odroid.com/odroid-xu4/application_note/gpio/wiringpi) library.


# Installation

To install, just run following:

```
pip install dht11
```


# Usage

1. Instantiate the `DHT11` class with the pin number as constructor parameter.
2. Call `read()` method, which will return `DHT11Result` object with actual values and error code.

For example:

```python
import RPi.GPIO as GPIO
import dht11

# initialize GPIO
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)
GPIO.cleanup()

# read data using pin 14
instance = dht11.DHT11(pin = 14)
result = instance.read()

if result.is_valid():
    print("Temperature: %-3.1f C" % result.temperature)
    print("Humidity: %-3.1f %%" % result.humidity)
else:
    print("Error: %d" % result.error_code)
```

For working example, see `dht11_example.py` (you probably need to adjust pin for your configuration)


# License

Keeping aligned with the original project this repo was forked from, this project remains licensed under the terms of the MIT license.


# Credits & Mentions

## DHT11 Python Library by Szazo

This project was forked from the [DHT11 Python](https://github.com/szazo/DHT11_Python) repo by [szazo](https://github.com/szazo). Many thanks go out to szazo for the incredible work in his project for using the DHT11 temperature and humidity sensor on the Raspberry Pi platform in a complete python implementation. Go check out his other projects, and be sure to show him some love while you're there!

## ODROID WiringPy Python Wrapper Port

ODROID provides a port of the WiringPi project, modified to work on the ODROID platform, through their Ubuntu PPA as well as Github account. This provides all of the same powerful features of WiringPi, with a Python wrapper, already configured to work with ODROID's GPIO pins. For more information and installation instructions, please visit the [ODROID Wiki](https://wiki.odroid.com/odroid-xu4/application_note/gpio/wiringpi).
