# FreeBSD-Steam-Tips
Just a FreeBSD repo dedicated to giving tips about Steam on FreeBSD


## Intro
Short and simple, FreeBSD is currently limited to a March build of Steam because of a steamwebhelper thingy... so uncool.
However I can't get into specifics but I found a workaround on how ya can get the latest build of Steam running on FreeBSD. Yay!

~~* You'll need to reboot a lot btw!~~ Is what I would have said if Alexander wouldn't have suggested a better solution.

### Software you'll need:

1. So start by installing the dev branch of wine with ```pkg install wine-devel```

2. After that make sure to install Mizuma, a cool wine frontend (we actually need to build this from ports to avoid dependency clashes, and modify the Makefile). First, do ```cd /usr/ports/games/mizuma``` and then do ```ee Makefile```. Once you are in the Makefile, navigate to ```RUN_DEPENDS=``` and then remove wine and wine-mono as dependencies, as shown below:
```
RUN_DEPENDS=    7zz:archivers/7-zip \
                bash:shells/bash \
                vulkaninfo:graphics/vulkan-tools \
                winetricks:emulators/winetricks \
                xdg-open:devel/xdg-utils \
                zenity:x11/zenity
```
Then, run ```make install```!

3. After all of that we want to install wine-proton ```pkg install wine-proton``` (Makes games a ton faster compared to base wine)

4. Make sure you install the 32 bit versions of both wine and proton ```/usr/local/wine-proton/bin/pkg32.sh install wine-proton wine-devel mesa-dri``` (Don't worry about the "/" at the start if you are 
unfamiliar, just copy this exactly into your terminal!)

## Going along

5. So now, run Mizuma in your terminal by typing ```Mizuma``` and go through the initial setup process, once you reach the menu, you'll need to click on Other, and then edit configuration file. Find the line "AllowLib32Maintenance" and edit Yes to be No. This is so Mizuma doesn't override wine-devel. After doing this, please also repeat step 4 again, because Mizuma may have overriden the 32 bit wine-devel.

6. Now we need to replace a file in our Mizuma library, so download this file: ```fetch https://raw.githubusercontent.com/coolerguy71/FreeBSD-Steam-Tips/main/Steam``` and then go to the directory ~/.local/share/Mizutamari/Library and copy the file you downloaded into this folder. 

7. It's time to start installing Steam! Now, open Mizuma, navigate to Installation, then scroll until you find Steam. Go through all of the options, and when steam goes past "Extracting Update" and the window closes, click on Kill Wine in the Mizuma menu. 

8. Open Mizuma again, click on Launcher < Steam, wait around 10 seconds, (to make sure the wine-devel configuration bakes in well) and then kill Wine.

9. Time to start modifying Steam to use Proton. Now, go to Other < Edit configuration file again, and now at the final line, chance /usr/local/bin to be /usr/local/wine-proton/bin. Then, open Steam, and kill Wine once again!

10. We'll need to adjust pulseaudio to work with Proton in this prefix! Run: ```WINEPREFIX=~/.local/share/Mizutamari/Games/Steam WINE=/usr/local/wine-proton/bin/wine winetricks sound=pulse``` this will set the sound to use pulseaudio, so we can hear things in our games.

11.Now, let's open Steam yet again, and we should have success. We should see the Steam login prompt. Hope you found this tutorial useful!

## Epilogue

So yeah, I was worried about the old steam build decaying, and was also worried about the potential malware associated with Archive.org, and thankfully, we now have a way to officially download Steam, and the latest version!

Bye!

- coolerguy71 (blue mode)
