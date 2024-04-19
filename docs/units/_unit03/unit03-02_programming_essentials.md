---
title: Writing code
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

In the last unit, you became familiar with the GPIOs. The basic principle is that these pins can be programmed, here demonstrated in Python. After connecting your sensor to the pins (see unit02-04), you first must:

1) mport the RPi.GPIO module: This module is necessary to control the GPIO pins. Import it using:

```
import RPi.GPIO as GPIO
```

2) set your numbering scheme

When you're working with Raspberry Pi GPIO pins, you have two numbering schemes to choose from:

BCM (Broadcom) numbering scheme: This refers to the numbering system of the Broadcom SOC (System on Chip) used in Raspberry Pi. In this scheme, each GPIO pin is identified by its Broadcom SOC channel number, which is a consistent numbering across different Raspberry Pi models. For example, GPIO pin 18 is always GPIO 18 in the BCM numbering scheme, regardless of the specific Raspberry Pi model you're using.

Board numbering scheme: In this scheme, the pins are numbered according to their physical positions on the Raspberry Pi's GPIO header. Pin 1 is at one corner of the GPIO header, and the numbering increases sequentially along the rows.

By default, the GPIO module in RPi.GPIO library uses the BCM numbering scheme. When you call GPIO.setmode(GPIO.BCM), you are explicitly setting the numbering scheme to Broadcom SOC channel numbers. This ensures consistency in your code, making it easier to write code that works across different Raspberry Pi models without needing to worry about differences in physical pin layouts.

```
GPIO.setmode(GPIO.BCM)
```


3) Define your GPIO pin:
Define the pin number you are using for your sensor according to the chosen numbering scheme[^1].

Here, we called it "sensor"
```
sensor_pin = 18
```

but could also be called tempsensor or similar 

```
tempsensor_pin = 18
```

4) Configure the pin as output or input:
Indicate whether you want to configure the specified pin as an output or input. 

When you set a pin to GPIO.OUT, it means you intend to control devices connected to this pin, such as LEDs, sensors, or other external components. You can then use that pin to send electrical signals to other devices connected to it. For example, you can use an output pin to turn on/off an LED, activate a relay, or provide power to a sensor. When the pin is set as an output, you can use the GPIO.output(pin, state) function to set its state to either high (3.3V) or low (0V), effectively turning it on or off.

On the other hand, when you configure a GPIO pin as an input (GPIO.setup(pin, GPIO.IN)), you're telling the Raspberry Pi that you want to read the state of that pin in your program. You typically use input pins to detect signals or changes in the electrical state from external devices connected to them. For example, you might connect a button to an input pin and use it to detect when the button is pressed or released.


For a more detailed instruction (in german), klick [here](https://tutorials-raspberrypi.de/raspberry-pi-gpio-erklaerung-beginner-programmierung-lernen/)[^2]

With these steps completed, you're ready to unleash your creativity, loop, and conquer.

[^1]: [hhttps://raspberrypi.stackexchange.com/questions/12966/what-is-the-difference-between-board-and-bcm-for-gpio-pin-numbering](hhttps://raspberrypi.stackexchange.com/questions/12966/what-is-the-difference-between-board-and-bcm-for-gpio-pin-numbering)
[^2]: [https://tutorials-raspberrypi.de/raspberry-pi-gpio-erklaerung-beginner-programmierung-lernen/](https://tutorials-raspberrypi.de/raspberry-pi-gpio-erklaerung-beginner-programmierung-lernen/)