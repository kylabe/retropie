![Sega CD Logo](http://img1.wikia.nocookie.net/__cb20120209224111/logopedia/images/d/da/Sega_CD_logo_(USA).png)
***
_The Sega CD was yet another add-on to the Sega Genesis. It was released in 1991._

***
## Emulators: [libretro-picodrive](https://github.com/libretro/picodrive)

## ROMS
Accepted File Extensions: **.smd .bin .md .zip .iso**

Place your Sega CD ROMS (.bin AND .cue) in
```
/home/pi/RetroPie/roms/segacd
```

If you don't have the corresponding .cue file in the same folder as your .bin file, your game may not have sound.

## BIOS

The BIOS filename is: **us_scd1_9210.bin**

Place this BIOS file in
```
/home/pi/RetroPie/BIOS
```
BIOS files that may also work are: eu_mcd1_9210.bin, jp_mcd1_9112.bin (Europe and Japan respectively)

## Controls

lr-picodrive utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/segacd/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) 