# The Computer

You will need the following things to get started:

* a computer that you aren't using that has a 64-bit processor
* a decent (10mbps up and down min) internet connection. wired is preferred but wi-fi works just as well
* a spare 8+ GB flash drive

this guide will show you how to install Linux onto your old PC, how to install and use Minecraft's server software, and give you general tips and tools for getting your server not only surviving but thriving. Let's get started!

## Doing some recon

Before we do anything, you're going to want to **boot up your old computer to get some useful information about it.** This tutorial could *technically* work on a macbook, but for all of my directions I'm going to be assuming that you have Windows 10 installed. Anything too old to meet this soft prerequisite probably isn't going to run amazingly, and i wouldn't expect a ton out of a macbook, but you're still welcome to try.

**This step is technically optional**, but if you skip it and find that your computer is underpowered and runs like garbage, you have been warned.

**Once you're logged into your old computer, press the start menu and search for "system information"**, click the thing that comes up first, and maximize the window. **Save a picture of this window or write down what it says,** because i'll be referencing terms from it in future discussions about what to do with your server.

You will be using linux as it takes less system resources to run than windows.

To get Linux onto your old computer, **make sure that your flash drive and old computer both don't contain any notable files or other important things you might want to keep, because we're going to be completely wiping them both.** Again, I want to warn you: to do this step we will need to **COMPLETELY ERASE** Windows and all files on both the disk and your old computer **FOREVER!** Please back up everything you don't want erased to a cloud service like Google Drive or to another USB flash/hard drive.

Lubuntu is really a better option here, as while Ubuntu is pretty, intuitive, and super easy to set up, it's known for being a relatively heavy OS that is going to be a slog on any middle-of-the-road computer older than, just spitballing, 2015. **Almost everyone should go with Lubuntu**, but if you're a brand-spanking-new beginner and you're timid about venturing into Techlandia, go with Ubuntu just to see what it's like and then graduate to something else later to speed up your server. Instructions are essentially the exact same between the two, so don't agonize over the choice.

* **[Lubuntu download link](https://lubuntu.me/downloads/)**

Next, you're going to want to **install [Etcher](https://www.balena.io/etcher/) onto your working computer**. This is the program that puts that file you just downloaded onto your flash drive in such a way that you can use it to install Linux. **Plug in your flash drive, start up Etcher, select "flash from file", and select the file you just downloaded.** Wait for the process to finish, and once it has, turn off your old computer if it isn't already.

Plug your flash drive into your old computer with it still off. Now turn it on. **What comes next is one of the only parts of this tutorial where it varies significantly from computer to computer.** You need to get into your BIOS, a sort of secret settings menu that modifies and manages the very basic and low-level parts of your computer such as, y'know, turning on. The problem is that not everyone agrees on how the user should be able to get there. **The moment your screen lights up, immediately start mashing the *f1, f2, escape, delete, and f12 keys*,** as these are the most common ones that computer manufacturers use to access this menu.

If you did it right, you should see a new screen pop up. Navigate through the menus with the on-screen instructions until you **find some sort of "boot" section.** Here there are a couple things you want to do. **You want to disable anything that's labelled "fast boot" and "secure boot"**, because these are features that can sometimes interfere with being able to modify your computer like this. Next, you should see some sort of "boot order" where it lists its priority for devices that it should try to boot from. **If it isn't already there, move your flash drive to the top of the list.** From here, do whatever the "save and exit" button is for your computer (it will tell you), and if it tries to reboot, turn it off by holding down the power button midway through. From here, re-insert your flash drive and turn it back on again.

**If all went well, you should see something labeled Lubuntu that looks completely different.** Just leave it still for a while, and let it boot up. If it doesn't do this on its own, press enter the first opportunity you get. Read whatever welcome message it gives you, and poke around for a while, if you like. This is a fully functioning desktop environment that comes with Firefox and a couple other things installed for you to use. Get comfortable with the interface, **sign into wifi if using a laptop** (if you can't find any option to then you may simply be out of luck, as a certain few laptops have wifi cards that just refuse to work with linux), and when you're ready, click the "install lubuntu" dekstop icon or button.

Follow the installer's simple instructions. When you're able to make a choice, you are going to want to select "erase entire disk". On the following screens, set your computer name (don't use spaces), username and password (make it a strong one!), and when given the opportunity, definitely check the "log in automatically" box. If you're doing Ubuntu, check the "minimal installation" box when you see it. Let the installer work its magic, which should only take around 11 minutes, and when it's finished, do as it says and turn the computer off and removing the flash drive.
