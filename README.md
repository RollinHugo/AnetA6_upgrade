# Anet A6 Upgrade
A simple todo list of resources for Anet A6 upgrading

## 1. Things to keep in mind:

- The Anet A6 shares a lot of design concepts with its sister the Anet A8. However, the latter is much more popular, and as such you will find a lot of resources for the A8, but much less for the A6. Keep in mind most A8 upgrades are compatible with the A6, but you might need some changes if it used 3D-printed bits.
- Some upgrades on this list concern safety. You **MUST** do them. They are not that hard or expensive, but your house is.

## 2. Safety upgrades

I will not cover the why (plenty of resources about the *Anet "firestarter" A6/A8* online). Most of them are related to fire safety.

### 2.1. Firmware

Older Anet firmware disabled some security features, so you should upgrade it. On the plus side, a newer Marlin firmware is much more user-friendly to navigate, and on my printer it removed the annoying beeps when the printer boot or when it is connected via USB. Nice! You can find information about Marlin here: https://marlinfw.org/ .
There are several way to upgrade it, detailled on this website. To be fair, I found this method to be quite simple on a factory ANET:

1. Go to the Marlin download page: https://marlinfw.org/meta/download/ and click on a version. This will send you to their github, within a more stable branch. Download/clone the repo.
3. Go to https://github.com/MarlinFirmware/Configurations and pick the previous selected Marlin version into the readme. This will bring you to the right branch. You only need a few files: dowload every ```.h``` file in ```config/examples/Anet/A6```.
5. Download and install Arduino IDE. Launch it. At launch, mine downloaded some libraries for about 5 minutes (progress in ther bottom terminal windows).
6. Connect your printer via USB. Once connected, the OS is given your Anet a port (```COM{some number}``` on windows, ```/dev/tyy{some stuff}``` on Linux). As you will need this number, I advise not to connect any other board to your computer, so you won't update another board by mistake. Also, make sure no other sofware is using your printer (Cura, Repetier-server, ...): only one device can access it at a time. Check if Arduino IDE recognize your A6. On mine, it recognize it as Anet V1 board or something like that. You might need to additionnal libs on your système.
7. On the Marlin repoo you cloned, open ```Marlin/Marlin.ino``` on the IDE. Check the code with the provided check option.
8. There will probably missing libraries, that you can most of the time install directly from the IDE. You check, if a library is missing install it, then check again until it's clear. The compilation process can be quite long.
9. Once everything is fine, upload to your board. Et voilà !

### 2.2. MOSFET upgrade

Basicaly, this will allow your ANET motherboard to control how much power is given to the heatbed, but that power will not transit by the MB anymore. The MB was not designed for this kind of power in mind, especially if you are using materials that need a higher bed temperature.
Here is a link for a tutorial done by more skilled people: https://3dprint.wiki/reprap/electronics/heatbed_mosfet. Read it wholly before making mistakes. Things I will highlight:
- The MOSFET is very cheap. Don't get fooled, and pick one like the one in the wiki, for less than 10 bucks.
- You will need to have some new cable. This needs to be strong cables able to withstand the power. Pick appropriate ones!

### 2.3. Power switch

This one is both for security and handiness. It adds a ON/OFF power switch to your printer, which is connected to your outlets with your usual power cable. Use a switch able to support the power, and I like to have a fuse in it.

### 2.4. Fans

I noticed my PSU was a bit hot (not that much, but still), and has no fan in it. I added fans for both the PSU and the motherboard. When choosing the fans:
- The PSU is 12V, so try to find 12V fans.
- They both goes pretty good withour fans, so a small airflow should suffice. I went for silent fans. They are less effective in my price range (<10€), but are still overkill.
- You can find lots of fan mounts for the PSU, but most of them are for 80mm fans.
- When shooping for fans, check the number of cable. Usually, <4 means your fan does not have PWM built-in and will go at 100%, which can be noisy as hell.

### 2.5. Bed connectors

Some people have issues with the conncetor on the bed, but as I use quite low temperatures on it, I have no issue with it. If you have, check this A8 wiki: https://3dprint.wiki/reprap/anet/a8/replace_hb_connector


## 3. Handy but simple upgrades

When looking for A6/A8 upgrades, you will notice that some people do so much upgrade you starts to wonder if there are still original pieces in it... It's nice, but I am not as committed. I made a small list of quality of life cheap upgrades you can do.

### 3.1. Silence...

OK so this printer is very noisy, and I don't like it. What you can do:
- Update to Marlin so that annoying start-up beep disappears.
- Replace the front fan of the extruder (not the axial one for the hot-end, but the "classic" facinf you). Size: 40x40x10mm. As it is always at 100%, it is noisy even if the printer is iddle. I went for a noctua one, but to be fair any reputable brand one is better than the cheap chinese one delivered with the machine.
- Replace the bearings. The original one are in metal, and quite noisy. I remplace them with some Igus one (pick LM8UU format). You need 4 for X and 4 for Y. I didn't feel like changing the Z axis one, which btw seems different.

### 3.2. Remote unplugging

TO BE UPDATED SOON:
I am working on a simple thing to add to the anet to be able to cut power remotly. There are commercial solutions, but they often come with a crappy app and are exepensive. I am currently trying a simple relay controled by the Pi.

### 3.3. Just a plank

My deck is crappy and not flat, and I need to move my printer now and then. The easiest way not to calibrate my A6 everytime I move stuff is to screaw it on a plank. I used a ~ 60x80x1cm plank which seems flat enough. There are 3D printable bits available online to fix a A6/A8, but tbh some wires and screw are just easier.

I will add things to this page, but the idea is "cheap, fast and easy stuff" to do, not full over-engineered upgrade :) PR welcomed, as always.
