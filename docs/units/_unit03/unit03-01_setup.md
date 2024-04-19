---
title: General set up
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---
*Programming of the Raspberry Pi*
<!--more-->

Computing devices and microcontrolers such as the Raspberry Pi, Raspberry Pi Pico, Raspberry Pi Zero, Arduino can be used  for a wide range of projects, from simple DIY electronics to advanced IoT (Internet of Things)[^1] applications. In this introduction, we'll explore the basics of configuring these devices and getting started with your projects.

Depending on the device you're using, you'll need to install the appropriate software.
The Raspberry Pi series of single-board computers (including Raspberry Pi Zero) runs on an operating system, such as Raspberry Pi OS (formerly known as Raspbian), Ubuntu, or other compatible Linux distributions. Raspberry Pi OS is the official operating system provided by the Raspberry Pi Foundation and is optimized for Raspberry Pi hardware. To effectively use them, install the RPI imager [^2] and then flash the operating system like onto a MicroSD card. For Arduino, you'll need to download and install the Arduino IDE on your computer.
{% include figure image_path="/assets/images/unit_images/unit03/wiring.png" caption="the Arduino IDE" %}

Note: in the course, your control unit will already be equipped with the needed sofware.

In terms of programming languages, Python is often used for Raspberry Pi; MicroPython for Raspberry Pi Pico and C/C++  for Arduino. It makes probably sense to use an integrated development environment (IDE) such as Juypiter, VisualStudioCode or PyCharm, which provide advanced code editing features such as syntax highlighting, code completion, and often  have built-in support for version control systems like Git.




---
[^1]: the network of physical objects or "things" embedded with sensors, software, and other technologies that enable them to connect and exchange data with other devices and systems over the internet.

[^2]: [ https://www.raspberrypi.com/software/]( https://www.raspberrypi.com/software/)