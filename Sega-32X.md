***
![sega32x](https://cloud.githubusercontent.com/assets/10035308/12212917/3dc2888e-b62d-11e5-8b2c-294b533f838b.png)
***
_The Sega 32X was released as an add-on for the Sega Genesis in 1994. There was a whopping total of 40 games for this console- it was considered a commercial failure._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-picodrive](https://github.com/libretro/picodrive) | sega32x  | .32x .smd .bin .md | none | /opt/retropie/configs/sega32x/retroarch.cfg |

## Emulator: [lr-picodrive](https://github.com/libretro/picodrive)

## ROMS

Accepted File Extensions: **.32x .smd .bin .md**

Place your Sega 32X ROMs in
```
/home/pi/RetroPie/roms/sega32x
```
## Controls

lr-picodrive utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/sega32x/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### Configuring a 6 button controller

First you need to tell retroarch to use 6 buttons, because the default is to use 3.

Launch a Sega 32X game and go to the Retroarch menu (default mapping: `select + x`). Go to `Quick Menu -> Core Options` and set the two input devices to `6 button pad`. Then exit the Retroarch menu. Once you quit the game, the configuration will be saved within the `retroarch-core-options.cfg` file under `/opt/retropie/configs/all`. You do not need to edit this file. These core options will also take affect on any other system which you may use lr-picodrive for (eg. Sega Megadrive, Sega CD).

### 3 Button Genesis/MegaDrive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/MegaDrive Controller

![genesis6btn](https://cloud.githubusercontent.com/assets/10035308/7336429/7e524110-ebbb-11e4-8777-05a824384d34.png)

### 6 Button Genesis/MegaDrive ArcadePad Controller

![megadrive6btnarcadepaddiagram](https://cloud.githubusercontent.com/assets/10035308/8268483/8b1b6dae-1744-11e5-9407-df58e2a81aad.png)