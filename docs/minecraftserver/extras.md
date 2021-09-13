# To infinity and beyond

We now have a perfectly functional 1.17 minecraft server, but a barebones one. There are a lot of things we can do to make it run faster (especially on older hardware), lag less, and be more fun and usable for you and your friends.

## Administrative setup

**You should probably op yourself. Join your server** by putting its hostname into direct connect in the multiplayer window. **Go to your Minecraft server's console (remember, log in with putty and do screen -r) and type `op yourname`** to give yourself operator permissions.

Your server also has a server.properties file that you can edit for all kinds of special settings that are detailed on the [wiki](https://minecraft.fandom.com/wiki/Server.properties). To edit text files over SSH, use `nano filename`, and use the hints on screen for keyboard shortcuts, because they'll be different from what you're used to.

## Let your friends connect over the internet

For one thing, **you're going to want to port forward in order to allow friends who aren't on your home wifi network to connect over the internet**. This is a process that differs a lot from router to router, but essentially, you're going to want to find some quick tutorial online and edit your router settings accordingly. **To see if it worked, go to <https://canyouseeme.org/> and type in port 25565 while the minecraft server is running. If it worked, the IP under "your IP" is what you're going to give to your friends to connect.**

## Vanilla-friendly mods and tweaks on Fabric

Like I mentioned earlier, FabricMC is great for running modded minecraft servers, if that's your plan. You simply need to drop the .jar that you download from curseforge or wherever else into the "mods" folder, and then make sure that all of your friends also have that mod installed. To get files onto your server from your normal computer, the easiest option would be to open up powershell, then type `pscp <path-to-file-on-your-computer> SERVERUSERNAME@SERVERHOSTNAME:/home/<path-to-where-you-want-to-send-the-file>`. For mods, the latter half of the command will be `/home/mcserv/mods`, while for datapacks it will be `/home/mcserv/world/datapacks`.

That being said, there are a ton of honestly must-have mods for Fabric servers that just plain make your server work better and lag less. All of the following links and lists are mods that don't require people connecting to have anything special installed at all, and are at the time of writing compatible with 1.17. At the end I provide one big zip file containing every mod that I use on my server for easy copy-paste installation. Enjoy!

* [List of performance mods for both Forge and Fabric for many versions of minecraft](https://gist.github.com/alkyaly/02830c560d15256855bc529e1e232e88)

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

## Quick glossary of Linux commands

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
