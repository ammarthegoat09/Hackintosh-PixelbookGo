# Hackintosh-PixelbookGo
A simple, beginner friendly, guide to install macOS onto your Pixelbook Go as well as a Pixelbook.

# Credits
This repository was made with [@olm3ca](https://github.com/olm3ca)'s testing as well as [@Interstellar750](https://github.com/Interstellar750)'s EFI folder. Please give these two as much support as possible, this repository would not have been made without them.

# Prerequisites
(1.   A Pixelbook or Pixelbook Go (Duh!).

(2.   A spare computer. Doesn't matter the operating system. We'll need it to mkae the macOS bootable USB.

(3.   A USB flash drive with at least 8GB of free storage as well as a USB-C to USB-A adapter.

(4.   An internet connection.

(5.   A willingness that you, the user, know that flashing firmware and installing 3rd party operating systems can potentially damage or destroy your Pixelbook.

(6.   A T3 and T5 Torx screwdriver. 

(7.   Patience. For most users, it may take days, even weeks to achieve macOS on a Pixelbook. There will be a lot of trial and error.

# Device
I will be using my personal and testing Pixelbook Go for this guide. Most pictures will be from me. Some will be from other sources, such as Reddit.

# Specifications
i5-8200Y, 16GB RAM, 128GB eMMC storage.
If your Pixelbook doesn't have these specs, don't worry. This guide should be able to get the user macOS no matter the Pixelbook model. (Unless you are using the Pixelbook 512GB model. This specific model won't work for this guide due to the fact that it uses NVMe. If you are not using NVMe, you can continue on with no problems.)

# Disabiling write-protect

If you have already disabled write-protect on your Pixelbook, you can skip this. If you haven't, keep reading.

**What is write-protect and why do we need it disabled?**

In order to install macOS onto your Pixelbook, you're going to need to flash coreboot. Coreboot is an open-source, Free Software bootloader that is aimed to change the firmware on someones computer. In this case, we are installing coreboot so that way we can remove the limitations of ChromeOS firmware. But how are we going to do it? First, we are going to need disable write-protect. What is write-protect you may ask? Well, simplified, its just a mechanism on your Pixelbook (Chromebooks in general) that is meant to stop the user from flashing any 3rd party firmware.

**Enabiling developer mode**
Before we can disable write-protect, we need to make sure developer mode is on. If it already is, you can skip this. If not enabled, keep reading.

In order to enable developer mode, turn on your Pixelbook and click the three keys circled in the picture below at once.

![IMG_0481](https://github.com/user-attachments/assets/b783801a-e8a5-47f0-a809-7771fb098787)

Once you do that, you should see this on your screen:

![IMG_0482](https://github.com/user-attachments/assets/cab90be1-d749-4502-8d1a-2caff88c3d19)


At this screen, go to your keyboard on click Ctrl + D, then Enter. You will then be met with another screen. Click on the keys Ctrl + D again. Once you do all of that, wait for your Pixelbook to transition to developer mode. There will be a timer on the left corner of the screen. Wait for it to finish. You will then be able to use your Pixelbook, but with develpoer mode! But now, we're going to need to disable write-protect

There are two ways to disable write-protect on your Pixelbook:

(1. Temporarily disconnecting the battery and keeping it disconnected until we flash firmware (which is what we will be doing for the guide)

(2. Using a SuzyQ[able]. You can either [buy a SuzyQable](https://www.ebay.com/itm/316024978790) or [make your own](https://www.reddit.com/r/chrultrabook/comments/uaiz1q/making_a_chromeos_suzy_q_cable_tutorial/). You can use [this guide](https://github.com/yusefnapora/pixelbook-linux?tab=readme-ov-file) once you obtain the SuzyQable. Keep in mind that this guide is a bit outdated and the terminal they are using is not doable. You will have to use the terminal we will be using later on in this guide. Remember to only follow the ["Disabiling Write Protect"](https://github.com/yusefnapora/pixelbook-linux?tab=readme-ov-file) section of the guide.



In order to, temporarily, disconnect the battery on your Pixelbook, we need to do these things:

**Removing the back cover**

There will be 2 black (or white if your using a Pixelbook) strips covering the areas of the screws if you haven't opened your Pixelbook before. Remove those two black or white strips to gain access to the screws. For the Pixelbook Go, there will be 10 screws. For the Pixelbook, there will be 17 screws. You should see something like this:

![My Image](pixelbook_closed.jpg)

Remove all the screws with your T5 Torx screwdriver. Once you remove all the screws, take off the back cover and put it down CAREFULLY. There will be a black or orange strip connecting the cover to the motherboard. It is part of the battery, and ripping it will make your Pixelbook not be able to detect power unless plugged in (Trust me, it's not fun.). The strip should look like this:

(The strip on this Pixelbook Go is broken. The back cover should be more lowered and the strip should be connected)

![IMG_0470](https://github.com/user-attachments/assets/59b8ba4e-2cf5-482a-a20b-c623f3364bfb)

Next to the connected strip should be a green or yellow screw. Grab your T3 Torx screwdriver and unscrew it. Once you do that, remove the strip from the connector and reinstall the back cover.

You have now succesfully disconnected your battery and disabled write-protect! Once we finish flashing the firmware to your Pixelbook, you can connect the strip back. But, for now, you are going to have to keep your Pixelbook plugged in for these next steps. Make sure you have a charger with at least 45W of power.

# Flashing coreboot

Once you turn on your Pixelbook, log in, or log in as guest, make sure you're connected to the internet and click the keys Crtl + Alt + Refresh (which looks like a loop). Once you click the keys at the same time, you will be met with a terminal. If clicking those keys don't do anything, make sure Developer Mode is on. At this terminal, log in with the name "chronos". In order to flash coreboot, we will be using [Mrchromebox](https://docs.mrchromebox.tech)'s Firmware Utility Script. This script will allow us to flash the requrired firmware for coreboot on our Pixelbook or Pixelbook Go. Once you log into the terminal, type the following commands:

<pre> cd; curl -LO mrchromebox.tech/firmware-util.sh </pre>
<pre> sudo install -Dt /usr/local/bin -m 755 firmware-util.sh </pre>
<pre> sudo firmware-util.sh </pre>

After typing the commands, you should be met with this:

![IMG_0483](https://github.com/user-attachments/assets/73f6da08-1ea6-4029-a4d2-e064168666a5)

Before we proceed, plug in your USB flash drive to your Pixelbook. (DISCLAIMER! Make sure the flash drive you're using doesn't have any important data you need! This is because using the flash drive for this script will erase all of the data in it!)

At the script, type the number 2 and press enter. You will be met with some warnings. Accept all the warnings and select your plugged in flash drive. Now you have to wait. Make sure not the unplug the flash drive during the process unless prompted to. Once the flashing process is done, reset your computer.

Congrats! You have now flashed coreboot onto your Pixelbook/Pixelbook Go! Now, we can get into the process of making a bootable macOS installer. (You can also plug the orange/black strip back in for the battery)

# Creating the macOS installer

Now that we have coreboot, we can install our operating system, macOS. But, like any other operating system, we need to make a bootable USB. Comapred to other operating systems, creating a bootable flash drive for macOS is very complicated. However, the goal of this guide is for it to be beginner friendly, therefore, a majority of the things we are going to download are pre-made for our Pixelbook.

Before we start, [download Rufus](https://rufus.ie/en/). At Rufus, plug in your flash drive, make your boot selection "Non-bootable", make your partition scheme GPT, then click "START". This should only take a few seconds, and will remove all data from your flash drive. Delete the two files from your Rufus flash drive.

The first thing we need to do in order to make our installer is to go to [this](https://github.com/yusufklncc/Hackintosh-for-All-Computers?tab=readme-ov-file#macos-monterey) repository. Here, scroll down until you find the section "macOS Monterey". Download the installer. Then, [download Balena Etcher](https://etcher.balena.io). Then, at Balena Etcher, click on "Flash from file" and select the .raw file from the folder you downloaded earlier (the macOS installer). Then, select your flash drive and click on "Flash!". Once it finishes flashing, unplug your flash drive and plug it back in. Your flash drive should now be named "EFI" and should have a size of roughly 200 MB. Once we finish this, we must [download our EFI folder](https://github.com/Interstellar750/pixelbookgo_hackintosh/tree/main?tab=readme-ov-file). This folder is responsible for making both the installer and operating be functional, giving things such as Wi-Fi, Bluetooth, trackpad support, display, etc. Once you have downloaded the EFI folder, copy and paste it onto your flash drive. Once you have done that, eject the flash drive, and we can get started on installing macOS.
 
# Installing macOS

We are now going through the process of installing macOS! In order to even get to the installer, first, plug in your flash drive to your Pixelbook/Pixelbook Go. Then, turn it on. Once you see the coreboot logo pop up, click on Esc and you will be greeted to a menu. It should look like this:

<img width="1024" height="768" alt="edk2_main_menu" src="https://github.com/user-attachments/assets/61f033a2-742c-4782-9e67-21f7749849e5" />

With your arrow keys, navigate to the boot menu and select your flash drive. You should be greeted to this menu:

![IMG_0488](https://github.com/user-attachments/assets/e12d546a-f6e9-4b0d-aecc-787a1f5d4a7b)

Here, click the space bar and navigate to "Reset NVRAM". Your Pixelbook will reboot, and you will have to go back to the boot menu. Once you do that, at the menu, select "Install macOS Monterey (external)". Once selected, you will see a bunch of text spew out. This is normal and is called a verbose. This is useful for debugging in case you run into any problems. Wait for the verbose to finish. You will be greeted with an Apple logo and a loading bar. This should load quickly. Once that loads, you should be greeted with a language selector. Select your prefered language. You will then be at this menu:

<img width="1010" height="768" alt="1691566482900802" src="https://github.com/user-attachments/assets/73b113c0-1633-458e-974f-5af25b42174e" />

Here, connect to Wi-Fi, select "Disk Utility", click on the "View" button, and select "Show all devices"

<img width="1010" height="768" alt="1691566482900802" src="https://github.com/user-attachments/assets/dcfb6a85-13ec-4274-808d-43a3f260dd70" />

Then, select your eMMC. You can identify what your eMMC is by selecting the drive that has the same amount of storage as how it was when you had ChromeOS. This can be 64GB, 128GB, 256GB, or 512GB. Select it and on the top of the windows click the "Erase" button, wait for it to erase your disk, then click on the "Partition" button. There, click on the circle that contains your eMMC. If it doesn't let you apply the partiton, add a partiton by clicking the "+" button, selecting "Create partiton", then clicking the "-". You should be able to apply the partiton. Make sure your partiton scheme is APFS. After partitoning, exit Disk Utility and enter the macOS installer. Follow the prompts from the macOS installer and, once you actually start installing macOS, just wait. Make sure to keep watching your Pixelbook, because at some point, its gonna reboot.

Once your computer reboots, select your flash drive from the boot menu, again. Here, you will see an additional option named "macOS installer (external)". Select it, and wait for the verbose to finish. Once the verbose finishes, once again, you will be met with an Apple logo, except the loading bar takes much longer to finish. It should look like this:

![1619bfa2-99b7-49b0-b4be-efda8e50b864](https://github.com/user-attachments/assets/8201ee3e-78fe-4713-9c6e-e1dc5f523ae0)


This is just your Pixelbook finishing up the installation of macOS. Once this loading bar finishes, your Pixelbook will reboot.





