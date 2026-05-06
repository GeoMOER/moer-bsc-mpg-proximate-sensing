---
title: Programming - ssh workspace
published: true
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

To view your pictures and the folderstructure associated, you can use a ssh file system provider.

## Install Plugin

To view your pi's interior as a folder structure, you need to install an extension.

Go to the VS Code Extension section and search for "SSH FS" (SSH Folder System).
Click onto "Install". A folder symbol will appaer in the toolbar on the left hand side, if installed successfully.

{% include figure image_path="/assets/images/unit_images/unit03/ssh1.png" caption="Activating the ssh file system"%}

## Configurate SSH

Click onto the freshly obtained SSH FS symbol. There you'll find all connections, you have configurated.
Under "Configurations" use the "Create a SSH FS configuration" symbol to create a new SSH FS connection. Type in a preferred name of the new connection and save it.

{% include figure image_path="/assets/images/unit_images/unit03/ssh2.png" caption="Creating a new ssh file system connection"%}

To establish a functunal connection, you need to edit the configuration.

- Name: The name of your configuration
- Host: The Hostname or IP Adress as it shows in the Wifi connections
- Port: 22
- Root: ~
- Username: The lockin username given via the pi's setup
- Password: The lockin password given via the pi's setup

Save!

{% include figure image_path="/assets/images/unit_images/unit03/ssh3.png" caption="Edeting the new ssh file system connection"%}

Once your conecction is successfully established, it will show under "connections". You can add it to your workspace by clicking the "Add as workspace folder" symbol.

{% include figure image_path="/assets/images/unit_images/unit03/ssh4.png" caption="Add the new ssh file system connection to your workspace"%}


