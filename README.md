# FreeBSD-Steam-Tips
Just a FreeBSD repo dedicated to giving tips about Steam on FreeBSD


## Intro
Short and simple, FreeBSD is currently limited to a March build of Steam because of a steamwebhelper thingy... so uncool
However I can't get into specifics but I found a workaround on how ya can get the latest build of Steam running on FreeBSD. Yay!

## Actual Tutorial
* You'll need to reboot a lot btw!

### Software you'll need:
So start by installing the dev branch of wine with ```pkg install wine-devel```

After that make sure to install Mizuma, a cool wine frontend ```pkg install mizuma```

After allat we want to install wine-proton ```pkg install wine-proton``` (Makes games a ton faster compared to base wine)

Make sure you install the 32 bit versions of both wine and proton ```/usr/local/wine-proton/bin/pkg32.sh install wine-proton wine-devel mesa-dri``` (Don't worry about the "/" at the start if you are 
unfamiliar, just copy this exactly into your terminal!)

