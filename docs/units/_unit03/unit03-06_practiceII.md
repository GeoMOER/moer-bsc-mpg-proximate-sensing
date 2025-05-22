---
title: Programming - take scheduled time-lapse images
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

This guide walks you through setting up a headless Raspberry Pi Zero to take a burst of images at regular intervals. You can do this using only a cron job (Option A) or enhance it with a Witty Pi Mini for power control (Option B).

## Create sh script for operating the camera

First, create the image capture script:

```
sudo nano /usr/local/bin/capture-by-day.sh
```
This should open an empty .sh
Paste the following in there:
```
#!/bin/bash

# Base directory to store images
BASE_DIR="/home/moth/Pictures"

# Get current date info
TODAY=$(date +"%Y-%m-%d")
TIMESTAMP=$(date +"%H-%M-%S")

# Create directory for today's date if it doesn't exist
TARGET_DIR="$BASE_DIR/$TODAY"
mkdir -p "$TARGET_DIR"

for i in {1..10}; do
    TIMESTAMP=$(date +"%H-%M-%S")
    libcamera-jpeg -o "$BASE_DIR/$TODAY/image_$TIMESTAMP.jpg" --width 1920 --height 1080 -n
    sleep 30
done

```
Close it and make it executable:

```
sudo chmod +x /usr/local/bin/capture-by-day.sh

```

## Option A: cronjob only

This option uses cron to schedule the capture script without power management.


```
crontab -e
```

Add the job to run every 10 minutes:

```
*/10 * * * * /usr/local/bin/capture-burst.sh
```
To see how to configure other cron jobs, see [here](https://www.geeksforgeeks.org/crontab-in-linux-with-examples/)

## Option B: with witty pi


Use the Witty Pi to turn on the Pi, run the script at the boot, then shut down.

{% include figure image_path="/assets/images/unit_images/unit03/WittyPi_on_PiZero.png.jpg" caption=" Witty Pi ontop of Raspberry Pi Zero"%}

We can thus make the cronjob start at reboot:

```
@reboot /usr/local/bin/capture-by-day.sh
```

Now, let's configure the wittyPi-schedule:

```
~/wittypi/wittyPi.sh  #check whether the path is right for your installation
```
Now, synchronize the RTC with your system by typing "3".
With typing "13" you exit. Navigate to the wittypi folder and add another schedule.

```
BEGIN   2025-05-13 00:00:00  #make sure that's in the future
END     2025-06-01 00:00:00  #make sure that's in the future
ON      M10         # Turns on every 10th minute
OFF     +00:06      # Stays on for 6 minutes
```

Activate the schedule by opening ahain the wittyPi.sh:
```
~/wittypi/wittyPi.sh  #check whether the path is right for your installation
```
Select 6 and your new schedule

>**Note**: When you activate a schedule, the pi will shut down - this should be the last step. If you realize you want to change something, you have to switch it on again - the schedule will still run in the background. Switch it off by opening the wittypi shell, and selecting "12".










<!--
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
-->

