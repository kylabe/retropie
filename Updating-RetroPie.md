# Updating RetroPie

The conventional way to update RetroPie is through the setup script. 

The setup script can be accessed from the **RetroPie menu** in emulationstation. 

It can also be accessed from the terminal with 
```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```

**Before making any major updates it is important to make backups just in case (see backup options below).**

## Using the RetroPie Setup Script

![restropiesetupscript](https://cloud.githubusercontent.com/assets/10035308/10266202/c39fd7e0-6a10-11e5-80b1-74b642fe8441.png)

- **The very first thing** you'll want to do before you do anything is select **Update RetroPie-Setup Script** as this will update the latest changes to the setup script.

- **Binary Based Installation:** If you wish to do a full update of RetroPie, this is the option you should choose. a backup is highly recommended before choosing this option

- **Source-based installation:** very rarely if ever should you use this as it takes more than 24 hours to run and likely will end up with some broken non-working emulators due to unfixed bugs

- **Setup / Configuration:** this is where you can update configurations, install new themes, controller drivers, etc. many of these options are also on the retropie menu in emulationstation

- **Experimental Packages:** these are emulators and options that may be potentially unstable but are worth checking out if you are feeling ambitious

- **Install Individual Emulators from Binary or Source:** This is where you will update individual emulators- you will almost always update from binary as they are more frequently updated, have less bugs, and are much quicker to install. There will be rare occasions where you may need to update from source but when in doubt just choose binary and you should be fine. 

#### Latest SD image

If you are worried about conflicts during an update you can always just start with the latest fresh sd image and just copy all your files back over onto that instead of updating from an older image.

## Making a Backup (Option 1)

You can create an sd image of your current sd card with win32diskimager (if you're on windows)

- Plug your sd card into your laptop (you will need a sd card reader for this)
- Open win32diskimager as an administrator (you can right click on it to run as an administrator)

![runasadministrator](https://cloud.githubusercontent.com/assets/10035308/10266141/babb3420-6a0c-11e5-9f20-c26297b9fbbf.png)

- make sure you have the correct drive letter for your SD card! 
- define the file path that you want to save your .img backup as

![win32diskimager](https://cloud.githubusercontent.com/assets/10035308/10266156/79baadf6-6a0d-11e5-9c98-62211328c68a.png)

- Click **read** to create your backup. (after you've backed this image up if you screw something up later and want to start from this image you can just click write and it will write this sd image back to your sd card.)
- note if you have a 64GB sd card it will create a 64GB backup file even if you don't have it completely filled up. If you don't want a file that large see the next option.   

## Making a Backup (Option 2)

if you don't want to create a sd image you can just back up your bios, roms, and configuration files from the samba shares

![configs](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)