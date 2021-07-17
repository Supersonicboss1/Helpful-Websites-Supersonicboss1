# Setting up a Minecraft Server

You will need the following things to get started:

* a computer that you aren't using that has a 64-bit processor
* a decent (10mbps up and down min) internet connection. wired is preferred but wi-fi works just as well
* a spare 8+ GB flash drive

this guide will show you how to install Linux onto your old PC, how to install and use Minecraft's server software, and give you general tips and tools for getting your server not only surviving but thriving. Let's get started!

## **The Computer**

### Doing some recon

Before we do anything, you're going to want to **boot up your old computer to get some useful information about it.** This tutorial could *technically* work on a macbook, but for all of my directions I'm going to be assuming that you have Windows 10 installed. Anything too old to meet this soft prerequisite probably isn't going to run amazingly, and i wouldn't expect a ton out of a macbook, but you're still welcome to try.

**This step is technically optional**, but if you skip it and find that your computer is underpowered and runs like garbage, you have been warned.

**Once you're logged into your old computer, press the start menu and search for "system information"**, click the thing that comes up first, and maximize the window. **Save a picture of this window or write down what it says,** because i'll be referencing terms from it in future discussions about what to do with your server.

You will be using linux as it takes less system resources to run than windows.

To get Linux onto your old computer, **make sure that your flash drive and old computer both don't contain any notable files or other important things you might want to keep, because we're going to be completely wiping them both.** Again, I want to warn you: to do this step we will need to **COMPLETELY ERASE** Windows and all files on both the disk and your old computer **FOREVER!** Please back up everything you don't want erased to a cloud service like Google Drive or to another USB flash/hard drive.

Lubuntu is really a better option here, as while Ubuntu is pretty, intuitive, and super easy to set up, it's known for being a relatively heavy OS that is going to be a slog on any middle-of-the-road computer older than, just spitballing, 2015. **Almost everyone should go with Lubuntu**, but if you're a brand-spanking-new beginner and you're timid about venturing into Techlandia, go with Ubuntu just to see what it's like and then graduate to something else later to speed up your server. Instructions are essentially the exact same between the two, so don't agonize over the choice.

* **[Lubuntu download link](https://lubuntu.me/downloads/)**

Next, you're going to want to **install [Etcher](https://www.balena.io/etcher/) onto your working computer**. This is the program that puts that file you just downloaded onto your flash drive in such a way that you can use it to install Linux. **Plug in your flash drive, start up Etcher, select "flash from file", and select the file you just downloaded. Wait for the process to finish, and once it has, turn off your old computer if it isn't already.**

Plug your flash drive into your old computer with it still off. Now turn it on. **What comes next is one of the only parts of this tutorial where it varies significantly from computer to computer.** You need to get into your BIOS, a sort of secret settings menu that modifies and manages the very basic and low-level parts of your computer such as, y'know, turning on. The problem is that not everyone agrees on how the user should be able to get there. **The moment your screen lights up, immediately start mashing the *f1, f2, escape, delete, and f12 keys*,** as these are the most common ones that computer manufacturers use to access this menu. 

If you did it right, you should see a new screen pop up. **Navigate through the menus with the on-screen instructions until you find some sort of "boot" section.** Here there are a couple things you want to do. **You want to disable anything that's labelled "fast boot" and "secure boot"**, because these are features that can sometimes interfere with being able to modify your computer like this. **Next, you should see some sort of "boot order" where it lists its priority for devices that it should try to boot from. If it isn't already there, move your flash drive to the top of the list.** From here, do whatever the "save and exit" button is for your computer (it will tell you), and if it tries to reboot, turn it off by holding down the power button midway through. From here, re-insert your flash drive and turn it back on again.

**If all went well, you should see something labeled Lubuntu that looks completely different. Just leave it still for a while, and let it boot up. If it doesn't do this on its own, press enter the first opportunity you get.** Read whatever welcome message it gives you, and poke around for a while, if you like. This is a fully functioning desktop environment that comes with Firefox and a couple other things installed for you to use. Get comfortable with the interface, **sign into wifi if using a laptop** (if you can't find any option to then you may simply be out of luck, as a certain few laptops have wifi cards that just refuse to work with linux), and when you're ready, click the "install lubuntu" dekstop icon or button.

**Follow the installer's simple instructions. When you're able to make a choice, you are going to want to select "erase entire disk". On the following screens, set your computer name (don't use spaces), username and password (make it a strong one!), and when given the opportunity, definitely check the "log in automatically" box. If you're doing Ubuntu, check the "minimal installation" box when you see it. Let the installer work its magic, which should only take around 11 minutes, and when it's finished, do as it says and turn the computer off and removing the flash drive.**

## **The Minecraft Server**

### Installing Java

**Boot up your computer**. **Connect to the internet** if you haven't already. **Open up a terminal window** (by searching for it in the start menu in the bottom left of your screen, or by pressing the windows key and starting to type). You're going to **type in a handful of basic commands**. **If you want to copy-paste these from a browser window on your old computer, use ctrl+shift+c and ctrl+shift+v instead of your normal keyboard shortcuts,** as simple ctrl+c and ctrl+v have different meanings to a linux terminal.

Type in the following one after another to fully update your computer before we do anything else:

```sudo apt update```

```sudo apt upgrade```

Now install a couple of things that we need to run the server and to better manage it later on:

```sudo apt install openjdk-16-jre ssh screen```

When this is done, we're going to want a new folder to keep all of our Minecraft stuff in, in order to prevent issues and avoid clutter. To do this, `mkdir` ("make directory") a new folder called "mcserv" or whatever other name you want:

```mkdir mcserv```

### **Setting up your server**
There are various ways you can run a minecraft server depending on your needs and wants. You should note these are **not compatible with each other,** you can only run one at a time.

#### **Fabric**

Fabric is a lightweight mod loader that is very performant and a good option for beginners and small server, or if you want to use fabric mods. This tutorial only covers vanilla, but if you wanted to do modded minecraft, this installation method gives you a really easy way to do so later down the line.

To install fabric, run these commands one after another into your terminal:

`cd mcserv`

This changes the current folder the terminal is in to your minecraft server.

`curl https://maven.fabricmc.net/net/fabricmc/fabric-installer/0.7.4/fabric-installer-0.7.4.jar -o installer.jar` 

This command downloads the Fabric installer to a file called `server.jar`.

`java -jar installer.jar server -downloadMinecraft`

This command downloads the minecraft server files.

When it's done, a few more files should have shown up in that folder. Start the server with `java -jar fabric-server-launch.jar` (you will do this every time to start the server up from now on) and wait for the error message. Edit the eula file to have `eula=true` in it, and congratulations, **you have just finished installing a minimal Minecraft Fabric server on your old computer!**

#### **Forge**

Forge is a much heavier modloader that I would only recommend using if you have mods that you want to play which require forge. Forge does not currently support 1.17 or Java 16 (which is the version you have installed) so you will need to put in some extra effort to make it work.

TODO add forge guide

#### **Purpur**

Purpur is a fork (built on top of) of Tuinity, which is a fork of Paper, which is a fork of Spigot, which is a fork of Bukkit. Confusing, right? Essentially, all of these are improvements upon each other, usually in the performance of the server. I would only recommend using **Paper, Purpur, and Tuinity** as the rest tend to be outdated or slower.

Purpur will have much better performance than Vanilla and Forge, and similar performance to fabric with performance mods. The main reason to use Purpur is for **plugins.**

Plugins are similar to mods, with two key differences. First, **plugins are usually version agnostic**, meaning that they tend to work on almost any minecraft version released **after the plugin.** Second, **they never need to be installed on the client,** meaning your players will never need anything other than regular minecraft. While both Forge and Fabric have mods which also do this (see end of guide for fabric examples), there are many mods which need to be installed on both the client and server, and will cause errors if they are not.

## **Managing your server**

So, if you really wanted to, you could be done here. You could turn on this old computer, hook up a keyboard and monitor at all times, and run `cd mcserv` and `java -jar fabric-server-launch.jar` manually every time you want to boot up your server. But there are better ways of running a minecraft server, chief among them being going headless. In server terminology, "headless" means not connected to any peripherals (keyboard, mouse, monitor, etc). This is the ideal for servers, Minecraft or not, because they're meant to be left running passively for long periods of time.

### SSH

SSH (or Secure Shell) is a protocol for securely sending commands (like you've been doing) over a network, from one computer to another. **To allow SSH connections into our server, we are going to have to run `sudo systemctl enable` and then `sudo systemctl start ssh`. Then, to allow it through our firewall, we will run `sudo ufw allow ssh`. If this command gives an error, don't worry about it and move on to the next.**

Now that we have an SSH server set up, **we need an SSH client**: a piece of software that knows how to talk to our server and send commands to it. There are a lot of solutions for this, including [browser extensions](https://chrome.google.com/webstore/detail/secure-shell/iodihamcpbpeioajjeobimgagajmlibd) and built-in command line tools that come with Linux and MacOS. But **for windows users, the best option is probably PuTTY, which you can download [here.](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**

Once PuTTY is open,** set the connection type to SSH, the hostname to your server's hostname, and the port to 22. Click Open, log in with your server's username and password, and congratulations!** You're back at the terminal, except from another computer, and you can now go headless and unplug the keyboard, monitor, mouse, and whatever else from your server. **It will automatically log in whenever you boot it up, and instead of using clunky peripherals every time to manage your server, you can simply remotely log in with PuTTY** after waiting a few minutes for it to boot.


### Screen

We have a problem. **We can start the Minecraft part of the server with the same command as always, but if we close the PuTTY window after doing this, the Minecraft server will go down**. We don't want Minecraft to depend on whatever window it's being run from: we want to start it, leave it be, and check in on it when we need to.

**To accomplish this, we are using a program called `screen`**. It creates virtual "screens" for commands to run inside of that can be switched between at ease. We installed this earlier, so **go ahead and type `screen -S minecraft`** to create a new screen called "minecraft". **We are going to want to do this every time the computer itself is restarted. To access this screen, type `screen -r`,** which will bring you to a new (but now empty) terminal view. From this we will t**ype `cd mcserv` to switch to the Minecraft server's folder, and then we will run our regular java command to start the server** as always. If you plan on in any way exiting this window or closing PuTTY or shutting down your server, **do ctlr+a and then ctrl+d to "detach" this screen** and return you to the terminal window you were just at. **Remember those two commands: `screen -r` enters the Minecraft screen which has your console on it, while ctrl+a+d returns you to the normal command line for system maintenance.**

## To infinity and beyond

We now have a perfectly functional 1.17 minecraft server, but a barebones one. There are a lot of things we can do to make it run faster (especially on older hardware), lag less, and be more fun and usable for you and your friends. 

### Administrative setup
**You should probably op yourself. Join your server** by putting its hostname into direct connect in the multiplayer window. **Go to your Minecraft server's console (remember, log in with putty and do screen -r) and type `op yourname`** to give yourself operator permissions.

Your server also has a server.properties file that you can edit for all kinds of special settings that are detailed on the [wiki](https://minecraft.fandom.com/wiki/Server.properties). To edit text files over SSH, use `nano filename`, and use the hints on screen for keyboard shortcuts, because they'll be different from what you're used to.

### Let your friends connect over the internet
For one thing, **you're going to want to port forward in order to allow friends who aren't on your home wifi network to connect over the internet**. This is a process that differs a lot from router to router, but essentially, you're going to want to find some quick tutorial online and edit your router settings accordingly. **To see if it worked, go to https://canyouseeme.org/ and type in port 25565 while the minecraft server is running. If it worked, the IP under "your IP" is what you're going to give to your friends to connect.**

### Vanilla-friendly mods and tweaks on Fabric
Like I mentioned earlier, FabricMC is great for running modded minecraft servers, if that's your plan. You simply need to drop the .jar that you download from curseforge or wherever else into the "mods" folder, and then make sure that all of your friends also have that mod installed. To get files onto your server from your normal computer, the easiest option would be to open up powershell, then type `pscp <path-to-file-on-your-computer> SERVERUSERNAME@SERVERHOSTNAME:/home/<path-to-where-you-want-to-send-the-file>`. For mods, the latter half of the command will be `/home/mcserv/mods`, while for datapacks it will be `/home/mcserv/world/datapacks`.

That being said, there are a ton of honestly must-have mods for Fabric servers that just plain make your server work better and lag less. All of the following links and lists are mods that don't require people connecting to have anything special installed at all, and are at the time of writing compatible with 1.17. At the end I provide one big zip file containing every mod that I use on my server for easy copy-paste installation. Enjoy!

* [great list of 500 server-side mods that you can and should look through, has everything you could want](https://github.com/comp500/fabric-serverside-mods)

* [Fabric API:](https://www.curseforge.com/minecraft/mc-mods/fabric-api) Required by most mods other than optimization mods. Does not do anything on its own.
* [Lithium:](https://www.curseforge.com/minecraft/mc-mods/lithium) an optimization mod that greatly reduces lag, is used by the Hermitcraft server
* [Krypton:](https://github.com/astei/krypton) speeds up the networking code of Minecraft, and gives a pretty nice performance boost
* [Recipe Cache:](https://www.curseforge.com/minecraft/mc-mods/recipe-cache) greatly reduced lag caused by big crafting batches and furnaces
* [Starlight:](https://github.com/Spottedleaf/Starlight/releases) an experimental, currently-in-beta, may-cause-bugs rewrite of Minecraft's lighting engine that's worth trying if you're still struggling after installing all these other mods. Can greatly reduce server lag.
* [FabricTPA:](https://www.curseforge.com/minecraft/mc-mods/fabrictpa) Adds the /tpa teleport requesting that you know and love to your server.
* [Immersive Cursedness:](https://modrinth.com/mod/lyiXgXNm) Somewhat buggy mod that lets you see through to the other side of nether portals and even reach through and place blocks! Can be disabled per-person if it causes FPS drops or ghost block issues.
* [Edit Sign:](https://modrinth.com/mod/editsign) Edit signs by right-clicking on them. That's it!
* [Full zip file of all of the above mods here](https://mega.nz/file/1PxHSYBK#9WsaOZ8JMSKDZg_egxU4NZXHeQr6J3y0xGrNfF3Pug0)

I also run Vanilla Tweaks on my server. It's a great project that provides a lot of handy datapacks (as well as great resouce packs) that you can pick and choose like you're building a Subway sandwich. You can find it [here.](https://vanillatweaks.net)

### Quick glossary of Linux commands

`cd` - "Dhange Directory". Moves you into the folder that you specify.

`ls` - "List". Lists all files and folders inside of the folder that you're currently in.

`rm <filename>` - "Remove". Deletes a file. To delete folders, you have to use `rm -r`.

`mv <file/folder> <destination>` - "Move". Moves a file or folder to the specified destination. Can also be used to rename folders/files by typing, for example, `mv homework.txt homeworkfinal.txt` to rename "homework.txt" to "homeworkfinal.txt".

`cp <file/folder> <destination>` - "Copy". Copies a file much like `mv` but with keeping the original.

`unzip <filename>` - Does what you'd expect.

`reboot now` - Does what you'd expect. Other arguments can be used instead of "now" to scehdule a reboot. sometimes needs to be run with `sudo`.

`shutdown now` - Does what you'd expect.Other arguments can be used instead of "now" to scehdule a shutdown. sometimes needs to be run with `sudo`.

`man <commandname>` - "Manual". Opens up the manual pages for that command. Might not be ideal for brand-new beginners as opposed to googling "how do i do x", but it's always there, and it won't let you down if you take the time to read into it.

`java -jar fabric-server-launch.jar` - The command you will use to start the Minecraft server. Must have `cd`'d into the `mcserv` folder first.