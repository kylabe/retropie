![Gameboy Advance Logo](http://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Gameboy_advance_logo.svg/640px-Gameboy_advance_logo.svg.png)
***
The Game Boy Advance currently has 3 emulators: [gpSP](https://github.com/DPRCZ/gpsp), [libretro-gpSP](https://github.com/libretro/gpsp), and [libretro-vba-next](https://github.com/libretro/vba-next)
## BIOS file

The gpSP emulator needs a GBA BIOS file `gba_bios.bin` in the directory of the gpsp binary. The RetroPie SD-card image, e.g., has the gpsp binary located in `/home/pi/RetroPie/emulators/gpsp/raspberrypi/`. Copy your GBA BIOS file into this directory.

As of RetroPie 2.2, the binary is now located in `/opt/retropie/emulators/gpsp/raspberrypi/`. To place it here, you need root privileges.

## Controller Setup

Before moving to the acctual configuration of the controls, take note that gpSP seems to not support the hat on gamepads but buttons and joysticks seem fine. Check to see if gpSP has been updated to support it but don't be surprised if it does not work.

###Previous Version

From [here](https://github.com/petrockblog/RetroPie-Setup/issues/193#issuecomment-19900909):

It appears that gpsp is not run via libretro thus its not configured like the rest of RetroArch. My solution was to run gpsp from command line with no arguments (sudo ./~/RetroPie/emulators/gpsp/raspberrypi/gpsp ) and configure my buttons through the onscreen menu there. This generated a gpsp.cfg file (binary).

If you have a keyboard connected you can press [F10] and access the menu to setup the controller. You can also access the menu while in-game by holding [SELECT] and pressing [R Trigger] on your controller.

###Current Version

Apparently as of the latest version, the method above works fine, except that the file locations have moved. The emulators themselves have been moved to `/opt/retropi/emulators`. To configure your input, simply do `cd /opt/retropi/emulators/gpsp`, and then run the program with `./gpsp`. It will mention something about no game loaded and on the bottom says to press B or Select to return; use a keyboard to press Backspace. This will come up with a menu that you can use the arrow keys on a keyboard to navigate. 

Move down to "Configure gamepad input" if you want to configure gamepad input, or use the a simular message for configuring the keyboard. In the new menu, use the arrow keys to highlight a line and press Enter on the keyboard. It will wait for a button to be pressed and will map that button to the virtual button in the emulator. After it finds the button, move to the next line and repeat. When done, simply select "Back" at the bottom of the menu and then "Exit gpSP" to save the settings.

## Games not working/White Screen

From [here](https://github.com/petrockblog/RetroPie-Setup/issues/218):

GPSP uses a File called game_config.txt.

> What is this file??? game_config.txt is a database of settings on a
per-game basis. A couple of the settings are required to make games
work at all, but most of them are there to improve the performance of
a game. If a game doesn't work then look through the settings here,
but keep in mind that this file can not be used to fix a majority of
games, the ones that don't work because of emulator bugs. For those
you'll have to wait for a new release and hope it someday gets fixed.

This file is in the wrong folder on RetroPie. It is in `./~/RetroPie/emulators/gpsp/game_config.txt` but it needs to be in `./~/RetroPie/emulators/gpsp/raspberrypi/game_config.txt`. You need to fix this, otherwise you will get problems with some games/roms.

On the latest version this issue has been fixed and you don't need to do this step anymore.