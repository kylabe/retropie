# Retropie - Ubuntu 16.04 LTS x86 Flavor

## Description

A guide to build the retropie setup on Ubuntu 16.04 LTS x86. 

Tested with an Intel NUC Kit NUC5CPYH.

## Sections

  - [Section 1: Install Ubuntu 16.04 LTS](#section-1-install-ubuntu)
  - [Section 2: Setup Retropie](#section-2-install-retropie)
    - [Section 2.1: Download](#21-download)
    - [Section 2.2: Installation](#22-installation)
    - [Section 2.3: Configuration](#23-configuration)
  - [Section 3: FAQs](#section-3-faq)
    - [Section 3.1: Emulationstation hangs if shutdown/restart was selected](#31-hang)
    - [Section 3.2: Cannot install PS3 driver](#32-ps3)  
    - [Section 3.3: Screen blanks after some minutes](#33-configuration)
    - [Section 3.4: Ubuntu does not autologin](#34-autologin)
    - [Section 3.5: How to setup a splashscreen?](#35-splashscreen)
    - [Section 3.6: No audio](##36-noaudio)
    - [Section 3.7: My NUC or Intel Baytrail/Braswell powered device hangs (Ubuntu 15.10)](##37-hang)
    - [Section 3.8: No HDMI audio (Ubuntu 16.04)](##38-nohdmiaudio)

***

## Section 1: Install Ubuntu 16.04 LTS
    
Download and install Ubuntu 16.04 LTS. Iso image can be used to create a bootable DVD or a USB stick.
http://www.ubuntu.com/download/desktop

To run RetroPie-Setup user must be a member of group root/admin.

## Section 2: Setup Retropie

### Section 2.1: Download
    
I would recommend to update and upgrade the existing APT packages with
```
    sudo apt-get update && sudo apt-get upgrade
```
After that, we install the needed packages for the RetroPie setup script:
```
    sudo apt-get install -y git dialog
```
Then we download the latest RetroPie setup script with
```
    git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```
The script is executed with
```
    cd RetroPie-Setup
    sudo ./retropie_setup.sh
```
The screen should look like this then:

![4 0beta](https://cloud.githubusercontent.com/assets/10035308/16218285/f06f3ba8-3738-11e6-9ccc-be601172713b.png)

### Section 2.2: Installation

**Manage Packages >> Quick Install**

This will install the core and main packages which are equivalent to what is provided with the RetroPie SD image.

Now, you have to copy your rom files into the ROMs directory. If you followed the steps above the main directory for all ROMs is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a subdirectory for every emulated system, e.g., nes, snes, megadrive. Attention has to be taken for the extensions of the ROM files. All the information needed for each system is detailed in this wiki (see wiki home page or sidebar for systems)

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal

### Section 2.3: Configuration

You can go into Setup / Configuration and enable autostart as you like.

## Section 3: FAQs

### Section 3.1: Emulationstation hangs if shutdown/restart was selected

It is not possible to restart/shutdown if an sudo requests an password. To disable sudo password request add the line `$user ALL=(ALL) NOPASSWD:ALL` at the end of `/etc/sudoers`. Replace `$user`with the name of your current user.

### Section 3.2: Cannot install PS3 driver

Ubuntu has an builtin PS3 bluetooth driver. There is no need to install sixad. Make your bluetooth dongle discoverable. Connect your controller over usb. Now open "bluetooth system settings/add device". Select PS3 controller and click ok. Your controller should pair now if you press PS button.

### Section 3.3: Screen blanks after some minutes

Open Ubuntu system settings menu disable screensaver and screen lock timeouts.  

### Section 3.4: Ubuntu does not autologin

Open Ubuntu system settings menu and select user accounts. Enable autologin for current user.    

### Section 3.5: How to setup a splashscreen?

Use Plymouth to setup a splash screen:
https://wiki.ubuntu.com/Plymouth

### Section 3.6: No audio

Open Ubuntu system settings menu and select right audio output device.  

### Section 3.7: My NUC or Intel Baytrail/Braswell powered device hangs (Ubuntu 15.10)

The default kernel 4.1 of Ubuntu 15.10 tends to hang. It is a know bug:
https://bugs.freedesktop.org/show_bug.cgi?id=91629

Update to higher kernel version solves this problem:
http://sourcedigit.com/18333-how-to-install-linux-kernel-4-3-3-on-ubuntu-15-10-ubuntu-15-04/

### Section 3.8: No HDMI audio (Ubuntu 16.04)

Ubuntu 16.04 uses Pulseaudio 8 which has issues with HDMI if you suspend your device or change display resolutions at runtime. This problem will be solved with Ubuntu 16.10 and Pulseaudio 9. Mupen64plus runs a fullscreen resolution of 640x480. If your default resolution differs there will be a resolution switch and Pulseaudio will set another audio device. You can disable Pulseaudio auto output selection. Open /etc/pulse/default.pa and comment out the line:
```
#load-module module-switch-on-port-available
```
https://bugs.freedesktop.org/show_bug.cgi?id=93946#c36