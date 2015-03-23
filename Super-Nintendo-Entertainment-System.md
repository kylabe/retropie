![SNES Logo](http://www.levelgames.fr/media/catalog/category/Super_Nintendo_logo_copie_2.jpg)
***
_The Super Nintendo Entertainment System (or SNES) was a 4th generation video game console released by Nintendo in 1991. It is one of the most popular consoles._
***

## Emulators: [PiSNES](http://sourceforge.net/projects/pisnes/), [snes9x-rpi](https://github.com/joolswills/snes9x-rpi), [libretro-armsnes](https://github.com/rmaz/ARMSNES-libretro), [libretro-catsfc](https://github.com/libretro/CATSFC-libretro), [libretro-pocketsnes](https://github.com/libretro/pocketsnes-libretro), [libretro-snes9x-next](https://github.com/libretro/snes9x-next)

Yes- there are a bajillion SNES emulators. If you have a Pi 2, the preference is **lr-SNES9x-next**

## ROMS

Accepted File Extensions: **.smc .sfc .fig .swc .zip**

Place your SNES ROMs in
```
/home/pi/RetroPie/roms/snes
```



## Controls

### lr-armsnes, lr-catsfc, lr-pocketsnes, lr-snes9x-next

lr-armsnes, lr-catsfc, lr-pocketsnes, lr-snes9x-next all utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/snes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### PiSNES

Controller configurations are kept in a file named snes9x.cfg located in 
```
/opt/retropie/emulators/pisnes
```
**Example Configurations**
```shell
[Keyboard]
# Get codes from /usr/include/SDL/SDL_keysym.h
A_1=100
B_1=99
X_1=115
Y_1=120
L_1=97
R_1=102
START_1=13
SELECT_1=9
LEFT_1=276
RIGHT_1=275
UP_1=273
DOWN_1=274
QUIT=27
ACCEL=8

[Joystick]
# Get codes from "jstest /dev/input/js0"
# from package "joystick"
A_1=3
B_1=2
X_1=1
Y_1=0
L_1=4
R_1=6
START_1=9
SELECT_1=8
QUIT=99
ACCEL=7
QLOAD=10
QSAVE=11
#Joystick axis
JA_LR=0
JA_UD=1
```