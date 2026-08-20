# Configuring the hardware
The Introduction to Networking lesson uses Raspberry Pis to demonstrate creating a computer network out of network-enabled computing devices. The [Raspberry Pi Imager tool](https://www.raspberrypi.com/software/) is used to write Pi-OS images to the SD-cards used by the Raspberry Pi hardware. Instructors will need a computer running a Linux OS (e.g. Ubuntu) and with an SD-card slot. Microsoft Windows can struggle with the various partitions (boot and root) created by the Pi-OS imager and is not recommended.

## Process
Repeat this process for each Rasberry Pi used in the Carpentries Workshop.

Insert the SD card which will contain the Pi OS image into the SD card slot on the Linux computer. Open the Imager tool and select the Raspberry Pi hardware that's being used.
![Imager step 1](fig/imager-process-01.png)("alt=Select a target Raspberry Pi device")
![Imager step 1](fig/imager-process-02.png)("alt=Select a target Raspberry Pi device")

Choose an operating system. This lesson will use a version of Pi OS without the Gnome desktop environment - scroll down to "Raspberry Pi OS (other)" and select that.
![Imager step 1](fig/imager-process-03.png)("alt=Select a target Raspberry Pi device")

Choose "Raspberry Pi OS Lite (64-bit)".
![Imager step 1](fig/imager-process-04.png)("alt=Select a target Raspberry Pi device")

Select the storage device to write the OS image to. It's safest to select the "Exclude system drives" checkbox to avoid accidentally selecting system drives on the host computer. If you haven't inserted the SD card into the SD card slot, then do it here.
![Imager step 1](fig/imager-process-05.png)("alt=Select a target Raspberry Pi device")

Leave the hostname box blank. The lesson learners will be configuring this.
![Imager step 1](fig/imager-process-06.png)("alt=Select a target Raspberry Pi device")

Choose appropriate localisation parameters.
![Imager step 1](fig/imager-process-07.png)("alt=Select a target Raspberry Pi device")

Choose a username for the device. This can be anything, but this lesson uses `scnet` so it's suggested that you use this. Use `scnet` as the password too.
![Imager step 1](fig/imager-process-08.png)("alt=Select a target Raspberry Pi device")

Leave the SSID box blank. This is likely to be auto-completed with the SSID of the network the host computer is attached to, so delete this if it is.
![Imager step 1](fig/imager-process-09.png)("alt=Select a target Raspberry Pi device")

Enable SSH and choose "Use password authentication". This lesson won't use SSH key pairs.
![Imager step 1](fig/imager-process-10.png)("alt=Select a target Raspberry Pi device")

Don't enable Raspberry Pi Connect.
![Imager step 1](fig/imager-process-11.png)("alt=Select a target Raspberry Pi device")

At this stage we're ready to write the image. Select "Write".
![Imager step 1](fig/imager-process-12.png)("alt=Select a target Raspberry Pi device")

Imager will issue a final warning now that you're about to overwrite the SD card. Select "I UNDERSTAND, ERASE AND WRITE".
![Imager step 1](fig/imager-process-13.png)("alt=Select a target Raspberry Pi device")

Wait until the write is completed.
![Imager step 1](fig/imager-process-14.png)("alt=Select a target Raspberry Pi device")
![Imager step 1](fig/imager-process-15.png)("alt=Select a target Raspberry Pi device")

When the Imager tool completes the Pi-Os writing and validation step it will show a completion screen with details of the completed task. From here you can choose to write another SD card, or quit the application. Imager saves the configuration so upon re-opening the tool another SD card image can be written without going through this setup again.
![Imager step 15](fig/imager-process-16.png)("alt=Select a target Raspberry Pi device")
