---
title: Programming - practice
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

# Raspberry Pi Camera Monitoring
In ecology, it is often usefull or even necessary to get image data of the species of interest. Timelapse data, i.e., a a collection of sequential observations recorded over a period of time at specific intervals, can be especially useful. It allows us to observe changes or patterns that occur slowly over time, e.g., plant growth.

The Raspberry Pi Foundation has developed a series of ![cameras](https://www.raspberrypi.com/documentation/accessories/camera.html), which can be mounted to the Raspberry Pi computer. We can then program the computer to take pictures at specified times. If the Raspberry Pi is connected to the internet, we can even transfer the images to a remote folder, thus making the data instantly accessable.
We can't connect the RPi to the internet in the framework of this course, so we'll focus on some local demonstrations.

## Getting the Raspberry Pi started

As explained in unit03-01, when using the Raspberry Pi for the very first time, the first step is to install an operating system onto a sufficient boot medium, ideally a micro sd-card. This is done using the ![Raspberry Pi Imager](https://www.raspberrypi.com/software/) software. The Raspberry Pi Foundation provides a detailed ![tutorial](https://www.raspberrypi.com/documentation/computers/getting-started.html#install-an-operating-system) for this step. Today, this will be a pre-installed for you to directly start.

Now, simply plug your sd-card, camera, monitor, mouse, and keyboard into the Raspberry Pi and connect your power supply! Since we don't plan on connecting to the internet you can skip WiFi configuration.


## Try out the camera module
To have a look at all the options available use
```shell
libcamera-still --help
```
Now, use `libcamera-still` in combination with useful additions to save an image on your desktop.

<details><summary>Solution</summary>
<p>
```shell
libcamera-still -o Desktop/image.jpg
`</p>
</details>
``
Task 1: Try taking a few images with different specifications!

## Automating the Process

To have the Raspberry Pi take an image autamatically at specified time intervals, we can define a <b>cron job</b> to have the image taken as a background process.

First, we need to write the image command into a shell script stored on the Raspberry Pi. We'll do this using terminal commands:

```shell
# navigate into folder
cd ~/Documents

# use nano text editor to create new shell script
nano take_image.sh
```

You should now have created and opened a new file, called take_image.sh.
Now, you need to find a way how to save images automatically under a new name. Create two lines of code, which utilize ***Command substitution*** and allow you to save image with date as numbers. 

<details><summary>HINT 1</summary>
<p>

Command substitution: This means that the command inside the parentheses is executed, and its output is captured and used as the value of the variable on the left.  
`SOMENAME=$( command...)` 

</p>
</details>


<details><summary>HINT 2</summary>
<p>
The person who created the command to get the date was not very creative. 
</p>
</details>

<details><summary>HINT 3</summary>
<p>
The result of HINT1, is a shell variable that contains the result of a previous assignment. This can be used in the filename
</p>
</details>

<details><summary>SOLUTION</summary>
<p>

`DATE=$(date +"%Y-%m-%d_%H-%M")`  
`libcamera-still -o Pictures/"$DATE".jpg`

</p>
</details>

To execute this script simply enter the following into the terminal

```shell
bash ~/Documents/take_image.sh
```

Lastly, we need to set up a cron job. Use the command <code> crontab -e </code> to edit your crontab. Read the information provided in your crontab and try having the script executed once every minute / all 10 minutes and when both worked, at the full hour !


## Test 
Now with a working Time-lapse Camera, test different settings (distances to the camera, camera type, background etc)