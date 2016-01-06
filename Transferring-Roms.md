# ROMS

ROMs stand for Read Only Memory. ROMs are essentially digital versions of old game cartridges which allow you to play games on emulators (software that mimics your old gaming consoles.) There are many issues involving Copyrights laws regarding the usage of ROMs, as a result in order to preserve the integrity and longevity of the  RetroPie project, the locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood- Google is your friend.

## Copying via SSH connection

One way for copying ROMs on the SD card is via an [SSH connection](http://en.wikipedia.org/wiki/Secure_Shell). It is enabled per default in Raspbian and allows, for example, to remotely log into the RPi with a Terminal or to copy files between two computers.

In order to connect to your Raspberry, you need to know the IP address of it. To get this you can select the show ip option in the retropie in emulationstation, have a look at your router/switch logs, or you can exit EmulationStation on the RPi and type 

```shell
ifconfig
```
The IP address of the RPi is the one behind "eth0, inet addr". The default user name and password for the Raspbian distribution is "pi" and "raspberry", respectively.

To copy files, you can use the command line tool "scp" or a GUI like [WinSCP](http://winscp.net/eng/index.php) (for Windows) or [Cyberduck](http://cyberduck.ch/) (for MacOS).

The **directories for the ROM files** are located in ~/RetroPie/roms/SYSTEMNAME, where SYSTEMNAME is the short name of the corresponding system.

You can find additional information about remotely accessing the RPi in the [eLinux wiki](http://elinux.org/RPi_Remote_Access).

## Copying via Samba Shares

The RetroPie Setup allows to install and configure Samba shares for each installed emulator. You can access this function in the RetroPie Setup Script in the menu "Setup". After the installation it is possible to copy ROMs to the Raspberry by using the corresponding Samba shares.

easiest way to access is to go into "computer" folder on windows and in the top type:

```shell
\\RETROPIE
```

## Using USB-Stick

### Auto copy files from USB-stick

You also have the possibility to use a service that automatically copies ROMs from an USB stick into the correct directories. You can enable this service with the RetroPie Setup Script from within the "Setup" menu. If you are using the SD-card image download of the RetroPie Project, this copy service is already enabled. 

As a prerequisite you need to make sure that your USB stick is formatted to FAT32 (note that formatting will erase all data on your USB stick)

The service works as following: **Starting with RetroPie 3.0 you first need to create a folder called `retropie` on your USB stick.** After you've created the retropie folder on the USB stick, The first time you plug the USB stick into the the RPi, a ROM directory structure is generated on the USB stick, which only takes a few seconds. You can unplug the stick, put it into your PC and copy your ROMs into the corresponding directories on the USB stick. When you put the USB stick back into the RPi, the ROMs are automatically **synchronized** with the ROM folder on the RPi. When the flashing on your USB sticks ends (which indicates that no writing or reading activities are going on) you can unplug your USB stick.

[**Video Guide**](https://www.youtube.com/watch?v=OYMoxvbkYD4)  
  

<a href="https://www.youtube.com/watch?v=OYMoxvbkYD4
" target="_blank"><img src="https://i.ytimg.com/vi_webp/OYMoxvbkYD4/mqdefault.webp" 
alt="Adding roms to RetroPie with USB" width="300" height="190" border="10" /></a>

### Manually copy files from USB-stick

From RetroPie version 3.0 a file manager is available, it allows you to manually transfer files between USB-stick and Raspberry Pi SD card. File manager can be run from 'RetroPie' Emulationstation menu. Quick file manager (MC) guide can be found [here](http://www.thegeekstuff.com/2008/10/midnight-commander-mc-guide-powerful-text-based-file-manager-for-unix/). Your USB-stick should be mounted in `/media/usb`. The directories for the ROM files are located in `~/RetroPie/roms/SYSTEMNAME`, where `SYSTEMNAME` is the short name of the corresponding system.