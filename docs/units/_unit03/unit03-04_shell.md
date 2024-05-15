---
title: Programming - shell
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

The shell terminal on a Raspberry Pi is a text-based interface that allows you to interact with the operating system through typed commands. Shell is used when the task involves basic file operations, directory navigation, or system configuration changes. These scripts, ending on **.sh** are meant for quick, repetitive tasks that don't require complex logic or data handling. You're working directly with system environments, manipulating environment variables, or handling simple user interactions.

If your task requires more complex logic, such as loops, conditionals, or error handling beyond what is comfortable in a shell scrip, python is used.

If you have a monitor, keyboard, and mouse connected to your Raspberry Pi, you can access the terminal directly. You can access the Raspberry Pi's shell remotely using SSH (Secure Shell).

Here are some common commands:
- `ls`: Lists the contents of the current directory.
- `cd` directory_name: Changes the current directory to directory_name. Use cd .. to go up one level.
- `pwd`: Displays the current directory path.
- `mkdir directory_name`: Creates a new directory named directory_name.
- `rm file_name`: Removes a file named file_name. Use rm -r directory_name to remove a directory and its contents.
- `nano file_name`: Opens a text editor (nano) to create or edit a file named file_name.
- `cat file_name`: Displays the contents of file_name.
- `cp source destination`: Copies a file or directory from source to destination.
- `mv source destination`: Moves a file or directory from source to destination.
- `sudo command`: Executes command with superuser privileges, necessary for many system modifications.
- `apt-get update` and `apt-get upgrade`: Updates the list of available packages and upgrades installed packages to their latest versions.
- `raspi-config`: Opens the Raspberry Pi Software Configuration Tool, which allows you to configure various system settings like network options, interfacing options, and localization settings.
