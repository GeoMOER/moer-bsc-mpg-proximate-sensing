---
title:  the practice
published: false
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

## Flashing the SD card of our sensor box
Needed: SD Card, SD card reader

0) Optional: Install [Visual Studio Code](https://code.visualstudio.com/)  
1) Install and start the Raspberry Pi imager as admin  
2) Select "Raspberry Pi Zero" as model  
3) Select "Raspberry Pi OS lite (32-bit)" under OS  
4) Add a Hostname (PS-yournumber)  
5) Add a username and password (see Ilias)  
6) SSH Option:  

SSH (Secure Shell) is a secure way to remotely access the Raspberry Pi’s command line from another computer (Windows, macOS, Linux).

It lets you:
Control your Pi remotely over the network
Run commands
Transfer files (using tools like scp or sftp)


In normal use cases, it would be best to use SSH keys instead of passwords - they are way more secure. 
SSH keys come in pairs:

Public key: Goes on the Raspberry Pi
Private key: Stays on your computer

When you connect, the Pi checks if your private key matches the public key it has — if yes, you're granted access without a password.
In the course, however, we will use passwords for simplicity (see credentials file in Ilias) 

7) flash!

Instead of using the imager, you could also create an empty file with Notepad++ or similar, and safe it on the SD card as ssh (no extension)


<!--
Let's learn by examples!

1)  Reverse engineering:
    De-construct the **A**utomated **M**oth **T**rap, which is the 2nd version of the AMT used in [this publication](https://resjournals.onlinelibrary.wiley.com/doi/full/10.1111/icad.12662). Document every step with photos and short texts. 
    - What are the single components used for? (use e.g. google lens or similar tools)  
    - Which GPIO number is triggering the UV light?  
    - Which GPIO number is triggering the flash?  

2)  Read the Chapters **Introduction** and **Hardware** of the [Insect Detect DIY camera](https://maxsitt.github.io/insect-detect-docs/hardware/) by M. Sittinger.

3)  Compare both trap systems with your ideal trap and discuss the pros and cons of the components (Group discussion)
-->
