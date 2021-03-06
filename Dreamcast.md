***
![dreamcast](https://cloud.githubusercontent.com/assets/10035308/12191302/2612a414-b590-11e5-82e3-f39acc38eb71.png)
***
_The Sega Dreamcast is a 6th generation home video game console released by Sega in 1998. It is notably the last console that Sega produced._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Reicast](https://github.com/reicast/reicast-emulator) | dreamcast  | .cdi .gdi | dc_boot.bin, dc_flash.bin | /opt/retropie/configs/dreamcast/mappings |

## Emulator: [Reicast](https://github.com/reicast/reicast-emulator) 

It can be very laggy and buggy, but some games work great (see compatibility list below). Pi 2 is required.  

Audio is choppy and not great, and degrades the longer the emulator is in use.  Restarting the emulator (and ultimately the Pi) may become a good idea after a couple hours of gameplay. There is a memory leak somewhere in the Reicast code. Low screen resolution are recommended to get best performance. Performance suffers if HD resolutions are used.   

## ROMS

Accepted File Extensions: **.cdi .gdi** 

Place your Dreamcast ROMs in
```
/home/pi/RetroPie/roms/dreamcast
```

[**DREAMCAST COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AD91IcudqHP7dDmEXLO25Pzb85uUgAy4chU2QxlZBQk/edit?usp=sharing) feel free to contribute to the list.

## BIOS

The BIOS files needed are: **dc_boot.bin, dc_flash.bin**

Place your BIOS files in
```
/home/pi/RetroPie/BIOS
```

## Video Setup Guide  

<a href="https://www.youtube.com/watch?v=yAB0_kkaa5s
" target="_blank"><img src="https://i.ytimg.com/vi_webp/yAB0_kkaa5s/mqdefault.webp" 
alt="RetroPie Dreamcast emulation" width="300" height="190" border="10" /></a>  

RetroPie 4.0 uses an output resolution independent render resolution of 640x480. Open `/home/pi/.reicast/emu.cfg` to modify render resolution.

## Tweaks

```
/opt/retropie/configs/all/autoconf.cfg
```
Option | Description | Value
--- | --- | ---
reicast_input | enable input auto configuration | (0/1)

## VMUs

VMUs are stored as .BIN files under `/home/pi/.reicast/`, and will be automatically created the first time you run Reicast without VMU files.  

On occasion, these VMUs do not get formatted quite right during creation, and the Dreamcast can't save or load data from them.  They just need to be reformatted -- run the `SYSTEMMANAGER` entry in the EmulationStation Dreamcast menu and / or see [this post](http://blog.petrockblock.com/forums/topic/configuring-controllers-in-reicast/page/2/#post-99715) for details.

## Controls
Starting with RetroPie 3.3 controls for the Dreamcast Emulator are automatically configured when you configure your controls through emulationstation.

![sega_dreamcast_diagram](https://cloud.githubusercontent.com/assets/10035308/16599638/7f411634-42c0-11e6-811c-456f02b2ea47.png)

Controls can be mapped via the `/home/pi/.reicast/emu.cfg` file. An example mapping for a PS3 controller is below for reference:

**PlayStation 3 Controller**

```
[PLAYSTATION(R)3 Controller]
button.0=Btn_Z
button.1=Btn_C
button.2=Btn_D
button.3=Btn_Start
button.4=DPad_Up
button.5=DPad_Right
button.6=DPad_Down
button.7=DPad_Left
button.8=Axis_LT
button.9=Axis_RT
button.10=DPad2_Left
button.11=DPad2_Right
button.12=Btn_Y
button.13=Btn_B
button.14=Btn_A
button.15=Btn_X
button.16=Quit
axis.0=Axis_X
axis.1=Axis_Y
```
If mapping is not working correctly try changing controller name for: 
```
[Sony PLAYSTATION(R)3 Controller]
```
For Wireless PS3 Controller use: 
```
[PLAYSTATION(R)3 Controller (xx:xx:xx:xx:xx:xx)]
```
Replace xx:xx:xx:xx:xx:xx with your own controller mac address

Press ctrl+c to exit- Or map a Quit button (PS) as shown above :D 


**Xbox 360 Controller:**

```
[emulator]
mapping_name = Xbox Gamepad (userspace driver)
btn_escape = 0x13a

[dreamcast]
btn_a = 0x130h
btn_b = 0x131h
btn_c = 
btn_d = 0x139h
btn_x = 0x133h
btn_y = 0x134h
btn_z = 0x138h
btn_start = 0x13Bh
axis_x = 0x00
axis_y = 0x01
axis_trigger_left = 0x0a
axis_trigger_right = 0x09

[compat]
axis_dpad1_x = 0x10
axis_dpad1_y = 0x11
```

**iBuffalo USB controller** 

```
button.0=Btn_B
button.1=Btn_A
button.2=Btn_Y
button.3=Btn_X
button.4=DPad2_Left
button.5=DPad2_Right
button.6=Quit
button.7=Btn_Start
axis.0=Axis_X
axis.1=Axis_Y
```

**PS4 Controller:**

```
[emulator]
mapping_name = Sony Computer Entertainment Wireless Controller
btn_escape = 316

[dreamcast]
btn_a = 305
btn_b = 306
btn_x = 304
btn_y = 307
btn_start = 313
axis_x = 0
axis_y = 1
axis_trigger_left = 3
axis_trigger_right = 4

[compat]
axis_dpad1_x = 16
axis_dpad1_y = 17
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted = no
axis_trigger_right_inverted = no
axis_dpad1_y_inverted = no
axis_dpad1_x_inverted = no
```

**Akishop Ps 360+ Joystick**
```
[emulator]
mapping_name = Akishop Customs PS360+ v1.66
btn_escape = 316

[dreamcast]
btn_a = 306
btn_b = 305
btn_x = 307
btn_y = 304
btn_start = 312

[compat]
axis_dpad1_x = 16
axis_dpad1_x_inverted = no
axis_dpad1_y = 17
axis_dpad1_y_inverted = no
btn_trigger_left = 309
btn_trigger_right = 311
```

**Mobile Gamepad [EXPERIMENTAL]**
```
[emulator]
mapping_name = MobileGamePad
btn_escape = 0x13a

[dreamcast]
btn_a = 0x130
btn_b = 0x131
btn_c = 0x136
btn_d = 0x137
btn_x = 0x133
btn_y = 0x134
btn_z =
btn_start = 0x13b
btn_dpad1_left =
btn_dpad1_right =
btn_dpad1_up =
btn_dpad1_down =
btn_dpad2_left =
btn_dpad2_right =
btn_dpad2_up =
btn_dpad2_down =
axis_x = 0x00
axis_y = 0x01
axis_trigger_left =
axis_trigger_right =

[compat]
btn_trigger_left = 0x138
btn_trigger_right = 0x139
axis_dpad1_x =
axis_dpad1_y =
axis_dpad2_x =
axis_dpad2_y =
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted =
axis_trigger_right_inverted =
```

##For mapping non-standard controller via @Folly

run in terminal :
```
cd /opt/retropie/emulators/reicast/bin
```

Here is a script called 'reicast-joyconfig'
run it :
```
./reicast-joyconfig
```

Choose your joystick.
Now you can map your buttons.
When all is done it outputs the text for making a file in 
/home/pi/.reicast/mappings

It outputs something like this (numbers are in decimals not hexadecimal such as in other contoller.cfg's(0x13b)):
[emulator]
mapping_name = Your Gamepad
btn_escape = 316

[dreamcast]
.......etc

make a file in /home/pi/.reicast/mappings called controller_Your Gamepad.cfg and paste the text in this file.