**Please check the [FBA documentation](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha) for for basic information about controls and managing ROMs - this page is for specific information about the lr-fba-next emulator's features.**

lr-fba-next is a popular choice for the Raspberry Pi 2 and up, as it supports the latest FBA romset (v0.2.97.38), and a broad set of features. FBA also should always outperform MAME in the games they both support, as it is tailored for speed, rather than accuracy. Also, it is a libretro core, so enjoys all the benefits of that: centralised controller configurations, many customisation options, netplay, shader/overlay support, etc.

## System menu

By default, if you hold the Start button for a few seconds, the system menu appears. Here you can set various game options, typically including 'Free Play' modes, regional settings, etc. Settings are saved in .fs files in the ROMS directory for the system in use, and are loaded automatically on next use.

## Dipswitches

lr-fba-next exposes all the dipswitch options of any given game to libretro, allowing you to adjust them via the RetroArch GUI. Hold hotkey (by default, Select) & X (the top button) to access the GUI, and then Quick Menu > Options. You should be presented by a menu like: 

![](http://www.zimagez.com/full/aaa69d795c1a5e2d817defaa1cf6b75424d4e11b61c059d71a69dbf0077a5a4ba365eb42e08b34d8.php)

The dipswitches available will vary from game-to-game. Any changes made will be stored in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```

## Button rebinding

lr-fba-next supports a useful feature where you can rebind the keys for indidual games, without impacting the internal libretro hotkey macros (select & R = quicksave, etc). These rebinding options are accessed and saved in the same way as the dipswitches above.

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/libretro/libretro-fba).