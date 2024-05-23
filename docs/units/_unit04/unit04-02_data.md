---
title: Automation- data storage
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

How the data will be transferred will also determine whether your sensor box get’s fully automated or not. 

Data can be stored locally, be directly transferred, or a combination of both
Local storage refers to the use of physical storage devices, such as **SD cards**, hard disk drives (**HDDs**) or solid-state drives (**SSDs**), to store biodiversity data. Local storage is often cheaper than transferring the data, especially when it’s large amounts, because you don’t have to pay extra for mobile data. Data are written faster, and you do not have to struggle with network coverage. Of course, it has the very pressing disadvantage of *not being fully automated*. You have to visit the device to read out the data regularly, and you have <ins>no real-time-information</ins>. Also, if your local storage fails for some reason, or worse, crashes completely, all your data is lost. However, data can accumulate to vast amounts.


## Exercise: 
-	Let’s assume we’d have implemented high quality cameras and microphones. Use your mobile phones to calculate the average image size / average size of an audio file record for 1 minute, 2 minutes, 3 minutes.  
-	Now, create a table with different scenarios (e.g. taking a record every x minutes, every x hours, in the time span from xx to xx o’clock, X days) to plot the monthly amount of data (on Y Axis) vs. number of records (X Axis) in R.  
-	Use the standard telephone provider as an example – how expensive would your contract be, and where to draw the line where the monthly cost becomes higher than personel and travel costs if you assume you have 10 of your sensor boxes running within a forest ca. 6 km from your University (reachable by bike)?  


## Potential local data storage options

**SD cards** use non-volatile flash memory to store data, which means that they maintain data integrity without the need for a continuous power source. They are small and thus often used where compact size and portability are essential. However, they typically have lower storage capacities and slower read/write speeds compared to SSDs and HDDs.  

**HDDs (Hard Disk Drives)** use magnetic storage technology to store data on spinning magnetic disks (platters) and have higher storage capacities at a lower cost per gigabyte, making them suitable for storing large amounts of data that does not require frequent access. Though HDDs typically offer higher storage capacities at a lower cost per gigabyte compared to flash memory-based storage solutions like SSDs and flash drives, they have slower read/write speeds, higher latency, and are more susceptible to mechanical failure due to their moving parts. The primary concern for HDDs during a power loss is potential damage to the read/write heads and platters. If the power goes out suddenly, the heads might not park correctly, which can lead to physical damage. However, data is not lost.

**Solid State Drives (SSDs)** use flash memory technology similar to SD cards, but they are designed for use as internal or external storage devices in computers and servers. They offer significantly faster read/write speeds and lower latency compared to HDDs due to their lack of moving mechanical parts, but are more expensive. More importantly, SSDs are more susceptible to data corruption during a power outage, especially if the drive is writing data when the power loss occurs. This is because the flash memory cells can be left in an intermediate state. Some higher-end SSDs include capacitors and other mechanisms to provide a brief power reserve - making things more costly.

Instead of local storage, data may be transferred either to a cloud or your very own server.

## Potential remote data storage options

**A cloud** is a network of remote servers hosted on the internet to store, manage, and process data, rather than relying on local servers or personal computers. It provides scalable and on-demand access to computing resources and services. The provider cares for infrastructure, security, and maintenance. However, storing data off-site means trusting the cloud provider with sensitive information, which can raise concerns about data breaches and compliance with privacy regulations – which makes is often unsuitable for state facilities. While cloud services often operate on a pay-as-you-go model, long-term costs can add up, potentially becoming more expensive than maintaining an in-house server for large-scale or continuous usage. 

**A server**, such as an FTP server, is a computer that provides resources, data, and services to other computers (clients) over a network. An FTP server specifically enables the transfer of files between clients and the server using the File Transfer Protocol. It requires proper setup, maintenance, and security measures to function effectively and securely. One can set up your very own physical server, which has similarities to setting up a PC, but with additional considerations for reliability, security, and remote access. Alternatively, you can a server.
Both of these options need some kind of data transfer. 

Both of these options need some kind of data transfer. 



