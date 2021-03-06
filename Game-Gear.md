***
![gamegear](https://cloud.githubusercontent.com/assets/10035308/12191611/0512b71e-b594-11e5-9d4e-47ed58354ef4.png)
***
_The Sega Game Gear was an 8 bit handheld gaming console released in 1990_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | gamegear  | .gg | none | /opt/retropie/configs/gamegear/retroarch.cfg |
| [Osmose](https://github.com/RetroPie/osmose-rpi) | gamegear  | .gg | none | /home/pi/osmose_files/osmose.ini |

## Emulators: [Osmose](https://github.com/RetroPie/osmose-rpi), [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX)
The Osmose is tedious to configure controllers with. The lr-genesis-plus-gx will be the most convenient choice as it utilises RetroArch configurations.
## ROMS
Acceptable File Extensions: **.gg**

Place your Gamegear roms in
```
/home/pi/RetroPie/roms/gamegear
```
## Controls

### lr-genesis-plus-gx

lr-genesis-plus-gx utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gamegear/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![segagamegeardiagram](https://cloud.githubusercontent.com/assets/10035308/8245009/b4c87e72-15e5-11e5-8ee5-691daa4d1dd5.png)

### Osmose
Once you have run Osmose at least once, a configuration file call osmose.ini will be created at
```
/home/pi/osmose_files/osmose.ini
```
It will look something like this:
```shell
# Configuration Starts Here !

#
#  General emulation keys:
#

SCREENSHOT    = SDLK_F2
SOUNDSHOT     = SDLK_F1
QUIT          = SDLK_ESCAPE
TILESHOT      = SDLK_F3
DEBUGGER      = SDLK_d
PAUSE         = SDLK_p

#
# First Player PAD:
#

PAD1_UP       = SDLK_UP
PAD1_DOWN     = SDLK_DOWN
PAD1_LEFT     = SDLK_LEFT
PAD1_RIGHT    = SDLK_RIGHT
PAD1_BUTTON_A = SDLK_LCTRL
PAD1_BUTTON_B = SDLK_LALT

#
# Second Player PAD:
#

PAD2_UP       = SDLK_KP5
PAD2_DOWN     = SDLK_KP2
PAD2_LEFT     = SDLK_KP1
PAD2_RIGHT    = SDLK_KP3
PAD2_BUTTON_A = SDLK_n
PAD2_BUTTON_B = SDLK_b
```

The above controls only apply to the keyboard. Configuring controls for a gamepad must be done by editing the es_systems.cfg file
```
/etc/emulationstation/es_systems.cfg
```
add your specific controls in this format to the gamegear section:
```
osmose -joy 1 -joy1 1 -joy2 2 -joyquit 6
```
see [This Thread](http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=23550) for more details