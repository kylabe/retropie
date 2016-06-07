***
![gb](https://cloud.githubusercontent.com/assets/10035308/12191785/d743f5e4-b595-11e5-98dd-ca2ec58a1769.png)
***
_The Game Boy was released by Nintendo in 1989 thus kicking off the era of handheld gaming and Pokemon._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gb  | .gb | none | /opt/retropie/configs/gb/retroarch.cfg |

## Emulator: [lr-gambatte](https://github.com/libretro/gambatte-libretro)

lr-gambatte is a libretro port of Gambatte that utilises RetroArch configurations for your controller

## ROMS

Accepted File Extensions: **.gb**

Place your Game Boy ROMs in
```
/home/pi/RetroPie/roms/gb
```
## Controls

lr-gambatte utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gb/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![gameboy](https://cloud.githubusercontent.com/assets/10035308/7334402/bd640072-eb4e-11e4-8251-d2bc3b876153.png)

## How to change the color palette

Open the RetroArch RGUI by pressing **Select+X** on the controller, or **Hotkey+F1** on the keyboard then navigate to:

* Quick Menu
    * Core Options
        * Change `GB Colorization` to `internal` by pressing left or right
        * Select an `Internal Palette` with left and right

Press **B** to go back to the Quick Menu and **Resume Content**.

To make the change permanent, choose **Save Configuration** on the main RGUI menu.

It's also possible to edit `/opt/retropie/configs/all/retroarch-core-options.cfg` and set the palette like:

~~~
gambatte_gb_colorization = "internal"
gambatte_gb_internal_palette = "GBC - Grayscale"
~~~

The complete list of palettes can be found in the emulator core source:

~~~
GBC - Blue
GBC - Brown
GBC - Dark Blue
GBC - Dark Brown
GBC - Dark Green
GBC - Grayscale
GBC - Green
GBC - Inverted
GBC - Orange
GBC - Pastel Mix
GBC - Red
GBC - Yellow
Special 1
Special 2
Special 3
~~~

https://github.com/libretro/gambatte-libretro/blob/master/libgambatte/libretro/libretro.cpp