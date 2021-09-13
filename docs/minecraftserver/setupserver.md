# The Minecraft Server

## Installing Java

**Boot up your computer**. **Connect to the internet** if you haven't already. **Open up a terminal window** (by searching for it in the start menu in the bottom left of your screen, or by pressing the windows key and starting to type). You're going to **type in a handful of basic commands**. **If you want to copy-paste these from a browser window on your old computer, use ctrl+shift+c and ctrl+shift+v instead of your normal keyboard shortcuts,** as simple ctrl+c and ctrl+v have different meanings to a linux terminal.

Type in the following one after another to fully update your computer before we do anything else:

```sudo apt update```

```sudo apt upgrade```

Now install a couple of things that we need to run the server and to better manage it later on:

```sudo apt install openjdk-16-jre ssh screen```

When this is done, we're going to want a new folder to keep all of our Minecraft stuff in, in order to prevent issues and avoid clutter. To do this, `mkdir` ("make directory") a new folder called "mcserv" or whatever other name you want:

```mkdir mcserv```

## Setting up your server

There are various ways you can run a minecraft server depending on your needs and wants. You should note these are **not compatible with each other,** you can only run one at a time.

### Fabric

Fabric is a lightweight mod loader that is very performant and a good option for beginners and small server, or if you want to use fabric mods. This tutorial only covers vanilla, but if you wanted to do modded minecraft, this installation method gives you a really easy way to do so later down the line.

To install fabric, run these commands one after another into your terminal:

`cd mcserv`

This changes the current folder the terminal is in to your minecraft server.

`curl https://maven.fabricmc.net/net/fabricmc/fabric-installer/0.7.4/fabric-installer-0.7.4.jar -o installer.jar`

This command downloads the Fabric installer to a file called `server.jar`.

`java -jar installer.jar server -downloadMinecraft`

This command downloads the minecraft server files.

When it's done, a few more files should have shown up in that folder. Start the server with `java -jar fabric-server-launch.jar` (you will do this every time to start the server up from now on) and wait for the error message. Edit the eula file to have `eula=true` in it, and congratulations, **you have just finished installing a minimal Minecraft Fabric server on your old computer!**

### Forge

Forge is a much heavier modloader that I would only recommend using if you have mods that you want to play which require forge. Forge does not currently support 1.17 or Java 16 (which is the version you have installed) so you will need to put in some extra effort to make it work.

TODO add forge guide

### Purpur

Purpur is a fork (built on top of) of Tuinity, which is a fork of Paper, which is a fork of Spigot, which is a fork of Bukkit. Confusing, right? Essentially, all of these are improvements upon each other, usually in the performance of the server. I would only recommend using **Paper, Purpur, and Tuinity** as the rest tend to be outdated or slower.

Purpur will have much better performance than Vanilla and Forge, and similar performance to fabric with performance mods. The main reason to use Purpur is for **plugins.**

Plugins are similar to mods, with two key differences. First, **plugins are usually version agnostic**, meaning that they tend to work on almost any minecraft version released **after the plugin.** Second, **they never need to be installed on the client,** meaning your players will never need anything other than regular minecraft. While both Forge and Fabric have mods which also do this (see end of guide for fabric examples), there are many mods which need to be installed on both the client and server, and will cause errors if they are not.