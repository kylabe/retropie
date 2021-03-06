- [Why do some emulators not show up?](https://github.com/retropie/RetroPie-Setup/wiki/FAQ#why-do-some-emulators-not-show-up)
- [Why can't I SSH as root anymore?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore)
- [Where did the desktop go?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#where-did-the-desktop-go)
- [Why does shut down and reboot take ages?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-does-shut-down-and-reboot-take-ages)
- [How do I hide the boot text?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-hide-the-boot-text)
- [How do I boot to the desktop or Kodi](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ/#how-do-i-boot-to-the-desktop-or-kodi)
- [How do I remove the black borders](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ/#how-do-i-remove-the-black-borders)
- [How do I change which buttons to press to exit an emulator with a controller?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-change-which-buttons-to-press-to-exit-an-emulator-with-a-controller)
- [Does Super Mario All Stars work?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#does-super-mario-all-stars-work)
- [How do I extend the available space when upgrading to a larger SD card](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-extend-the-available-space-when-upgrading-to-a-larger-sd-card)
- [How would I start from command line, say, the SNES emulator by itself?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-would-i-start-from-command-line-say-the-snes-emulator-by-itself)
- [Is there another way to set up the gamepad for use, e.g., within the snes emulator?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#is-there-another-way-to-set-up-the-gamepad-for-use-eg-within-the-snes-emulator)
- [The PSX emulator reports no BIOS found. What do I do?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#the-psx-emulator-reports-no-bios-found-what-do-i-do)
- [Which memory split should I use?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#which-memory-split-should-i-use)
- [Why aren't my in-game saves working properly?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-arent-my-in-game-saves-working-properly)
- [Why Can't I Insert Coins in Arcade Emulators?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-insert-coins-in-arcade-emulators)

### Why do some emulators not show up?

In Emulation Station, only emulators with ROMs inside its respective folder will show up in the Emulation Station GUI (given that the specific emulator is installed). For example, for the Nintendo 64 emulator to show up, you must have at least one ROM in the `~/RetroPie/roms/n64/` folder. For ROM types supported by each emulator, go to the wiki page for that specific system/emulator. 

### Why can't I SSH as root anymore?

The root password is disabled by default (as is the case for Raspbian and many other linux distros). 

before setting a root password, the following must be edited

```sudo nano /etc/ssh/sshd_config```

look for 

```PermitRootLogin without-password```

change it to

```PermitRootLogin yes```

then ctrl+x to save, 

next set your root password:

```
sudo passwd root
 
```

restart your Pi to register your changes

see these posts for more details:

https://www.raspberrypi.org/documentation/linux/usage/root.md

http://elinux.org/R-Pi_Troubleshooting#I_don.27t_know_the_root_password

### Where did the desktop go?

The LXDE desktop environment was removed from the RetroPie image to keep it smaller.

It can easily be installed from the [RetroPie Setup Script](https://github.com/retropie/retropie-setup/wiki/Updating-RetroPie)

in **Setup >> Raspbian Related Tools >> Install desktop environment (LXDE)**

after installation it will be accessible from the ports menu of emulationstation or can be called from the command line with `startx`

![lxde](https://cloud.githubusercontent.com/assets/10035308/14362890/de6ad5f2-fcbe-11e5-9a4b-07e6a529145f.PNG)

You can also install it manually with:

`sudo apt-get install lxde`

if you want the Raspbian flavoured LXDE you can type

`sudo apt-get install lxde xorg policykit-1 raspberrypi-ui-mods`

For Raspbian Jessie you also need to install:

`sudo apt-get install xinit`

And then you can access it from the terminal by typing in

`startx`

After installation your pi will boot into the desktop environment, you can change the behaviour to boot into emulationstation by selecting the autostart option for emulationstation from option 3 of the setup script, or you can set the autologin to console option from the boot options of the raspi-config menu.

Note that failing to run startx after the installation may prevent other XWindow-based applications from starting (e.g. Micropolis port), so do launch the desktop after installation to ensure that it is fully set up.

### Why does shut down and reboot take ages?

Previous to RetroPie 3.4, there was an issue whereby EmulationStation was terminated on reboot/shut down, rather than shut down 'cleanly'. This has now been fixed, so every time you reboot/shut down EmulationStation rewrites all metadata about your roms, so that play counts, last-played dates, etc., are saved. This has the side-effect of the causing the whole process to take longer, relative to how many ROMs you have. MAME/FBA ROMs can often form the bulk of libraries, so it might be helpful to remove clones by [rebuilding your set with a custom parent-only DAT](https://github.com/retropie/retropie-setup/wiki/Managing-ROMs).

An option has been added starting with RetroPie 3.7 to decide whether or not you want metadata saved on exit.
![main menu](https://cloud.githubusercontent.com/assets/10035308/14507387/a7ee93b8-017f-11e6-94f2-af5a2e158079.png)
![metadata](https://cloud.githubusercontent.com/assets/10035308/14507388/a7fc1bfa-017f-11e6-8f01-8cfed5344542.png)

- **Save Metadata On Exit:** If on, it will read and write all the info for your roms which can lead to long boot and shutdown times if you have large romsets. If you turn it off it will not write those changes which means it also will not write how many times you've played a game, any new game scrapes, etc. This is on by default.

- **Parse Gamelists Only:** If on, it will only read the roms you have scraped, so if you add any new roms it will not look for them unless you turn this back off. it is off by default.

### How do I hide the boot text?

**NOTE that you should be comfortable with editing files in Linux as any wrong edits on the following file can break your boot sequence requiring a reimage of your SD card!**

`sudo nano /boot/cmdline.txt`

change `console=tty1` to `console=tty3` 

And add `quiet loglevel=3 logo.nologo` at the end.

**make sure it is all on the same line!!!** 

The logo.nologo option is what turns off the raspberries on boot.

You can also disable the rainbow splash at the beginning (not to be confused with the underpowered rainbow square the appears in the top right corner of your screen indicating you have an insufficient power supply)

Add `disable_splash=1` in `/boot/config.txt`

### How do I boot to the desktop or Kodi

In retropie setup script>>Configuration / tools>>autostart

![autostart](https://cloud.githubusercontent.com/assets/10035308/15987124/7699dbcc-2fda-11e6-8a1f-902e3177d782.png)

- **Start EmulationStation at Boot:** Boots into EmulationStation.
- **Start Kodi at Boot:** Boots into Kodi- if you exit Kodi you will be returned to EmulationStation.
- **Manually Edit /opt/retropie/configs/autostart.sh:** you can manually add other programs to start on boot.
- **Boot to text console (autologin):** Boots into the terminal.
- **Boot to Desktop:** If you have a desktop environment installed like LXDE this will boot into the desktop.

### How do I remove the black borders?

Depending on the resolution of your television you may get black borders around your tv. You can full the whole expanse of your screen by editing the overscan settings. Exit to the terminal with F4 or access your pi over [SSH](https://github.com/RetroPie/RetroPie-Setup/wiki/ssh)

```
sudo nano /boot/config.txt
```
uncomment (i.e. delete the `#` preceding the line) 

```
#disable_overscan=1
```

to

```
disable_overscan=1
```

save with `ctrl+x` 

then reboot. If it doesn't work then try messing with some of the other [overscan](http://elinux.org/R-Pi_Troubleshooting#Big_black_borders_around_small_image_on_HD_monitors) settings manually 
### How do I change which buttons to press to exit an emulator with a controller?

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games. The following defaults are set automatically the first time you set up your controller from emulationstation.

#### Default joypad hotkeys:
Hotkeys | Action | Code Example
| :---: | :---: | :---: |
Select | Hotkey | input_enable_hotkey_btn = "6"
Select+Start | Exit | input_exit_emulator_btn = "7"
Select+Right Shoulder | Save | input_save_state_btn = "5"
Select+Left Shoulder | Load | input_load_state_btn = "4"
Select+Right | Input State Slot Increase | input_state_slot_increase_btn = "h0right"
Select+Left | Input State Slot Decrease | input_state_slot_decrease_btn = "h0left"
Select+X | RGUI Menu | input_menu_toggle_btn = "3"
Select+B | Reset | input_reset_btn = "0"

You can adapt the above code example and choose the button number to your desired button for each hotkey function in the retroarch.cfg files for most systems (at least all the emulators that are part of RetroArch) 

You can change it per controller with your autoconfig file here 

```
/opt/retropie/configs/all/retroarch-joypads/yourgamepad.cfg
```

You can Hardcode it globally for all systems here:

```
/opt/retropie/configs/all/retroarch.cfg 
```

or set it by system

```
/opt/retropie/configs/SYSTEMNAME/retroarch.cfg
```

See [HERE](RetroArch-Configuration) for more information on custom controller configs

### Does Super Mario All Stars work?

The ROM does work with PocketSnes (RetroArch) and lr-snes9x-next.

From http://blog.petrockblock.com/2012/07/22/retropie-setup-an-initialization-script-for-retroarch-on-the-raspberry-pi/#comment-818063235:

> I found out that after the selection of a game, the control goes over to the second controller! This seems to be somehow a speciality of the All-Stars ROM. But at least, it is playable :-)

Alternatively, if you only have one controller (or play alone) you can do the following:

From http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=79083

> I managed to figure out a fix so the controls work in Super Mario All-Stars and also doesn't break other games (Mario Kart, Super Bomberman etc). This problem has been bugging me for ages and I had to figure out a way to play this game for nostalgia sake. This fix will unfortunately mean player two controls wont work for other games (but I play alone anyway and this is for people with one controller). Simply post this in your blank retroarch.cfg in the snes folder. P.S Remember to change the button numbers/axis for you own controller.

### How do I extend the available space when upgrading to a larger SD card

1. Navigate to the command line interface by either hitting F4 in EmulationStation or using the main menu to exit
1. Type in the following command: `sudo raspi-config`

1. Select option "1. Expand Filesystem"
1. Reboot your Raspberry Pi

### How would I start from command line, say, the SNES emulator by itself?

You can run a SNES rom by calling 

```
retroarch -L /opt/retropie/libretrocores/lr-pocketsnes/libretro.so /home/pi/RetroPie/roms/snes/nameofyourrom.smc
```

If you'd like keyboard configurations to work add
```
--config /opt/retropie/configs/all/retroarch.cfg
```

### Is there another way to set up the gamepad for use, e.g., within the snes emulator?

Follow the RetroArch-Configuration guide:

https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration

### The PSX emulator reports no BIOS found. What do I do?

Ensure the bios file(s) is/are all lowercase and put them in
```shell
/home/pi/RetroPie/BIOS
```

More information about PSX BIOS files can be found on the [PSX page](https://github.com/petrockblog/RetroPie-Setup/wiki/Playstation-1).

### Which memory split should I use?

Using the raspi-config or rpi-update script, one can change the RAM splitting for the Raspberry Pi. Depending on your hardware setup you might have to change your splitting.

From [ToadKing](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=112241#p112241):
> If you're on 224/32, you can't run it (i.e., RetroArch) on a HD display. You'll have to use the 192/64 split at least.

A Raspberry Pi B/B+/2 is highly recommended. The GPU should have at least 256MB RAM. If you have a Raspberry Pi A/A+  it is not possible to scrape games and use system themes. 

### Why aren't my in-game saves working properly?

All retroarch emulators use the same method to save to your .srm or SRAM. The default behavior is to only write to your srm file upon a clean exit back to emulationstation. This is done by default with the exit hotkey start+select. If the game happens to completely freeze or crash, it's likely that you will lose in-game progress even after saving.

Besides using save states, one optional method you can use to prevent this accidental loss in progress is the autosave_interval setting. This setting can be changed in `/opt/retropie/configs/all/retroarch.cfg`
either with the terminal, Configure Retroarch / Launch RetroArch RGUI under `settings->saving`, or Edit RetroPie/RetroArch configurations under `Manually edit Retroarch configurations`. Once autosave_interval is set to equal a number of seconds, retroarch will automatically write your save data to the srm file every interval of that number of seconds.

### Why Can't I Insert Coins in Arcade Emulators?

It's the Select button in RetroArch. By default, it's right shift. Note that this issue should now be fixed.

Sometimes there are conflicts between the hotkeys and insert coin buttons so they need to be swapped manually in the retroarch.cfg in order for the select key to insert coins properly. The hotkey button was originally intended to be an unused button but some controllers like snes controllers don't have extra buttons.

For example you can switch the hotkey button to a button that you don't use:

so in mame retroarch.cfg
```
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```

you could add 
```
input_enable_hotkey_btn = 5
```
which would make the hotkey the left bumper (on my controller- may be a different button for yours) then the select key should work for inserting coins. but in the future in order to exit mame I would then have to press left bumper+start as i changed my hotkey to the left bumper. 

You can do the same thing for fba-libretro
```
/opt/retropie/configs/fba/retroarch.cfg
```

Another simple workaround is to use player 2's select key to insert coins but it may not work for some games.

Related post  
http://blog.petrockblock.com/forums/topic/fba-retroarch-core-coin-controls/#post-93014