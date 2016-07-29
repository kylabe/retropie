# Arcade System Hardware
Spinners and Trackballs appear on the control panels of many arcade classics. Although MAME is often able to accommodate the use of a joystick instead, _many_ popular titles are best played with their native controls. Even the steering wheels on racing games can be thought of like a large spinner.

Spinners and Trackballs are often described together because of the way the work. Spinners operate by rotating a spindle which turns an encoder wheel. Optical sensors detect the movement of the encoder wheel and forward the speed and rotational direction to the arcade game. Trackballs are essentially the same but they have two spindles oriented perpendicular to one another. By rolling a ball that is in direct contact with the spindles, trackballs can provide two-dimensional input like a mouse. In this respect, a spinner is also like a mouse that only moves in a straight line (left/right or up/down).

# Hardware for Emulators
Because mouse input is ubiquitous on modern computers, spinners and trackballs translate nicely to emulators that can accept input from a mouse. For trackballs, the input is practically identical to a mouse. Spinners can also be setup like a mouse with separate X and Y tracking (like an Etch-a-Sketch).

Adding a USB mouse to a Raspberry Pi is trivial. Attaching a trackball or spinners requires a USB interface. Fortunately, arcade hardware is available that will work, and often comes with (or is compatible with) a USB interface. There are several options available from Ultimarc, Groovy Game Gear, Happ, and others. The key to making this hardware work on the Raspberry Pi is to ensure that the interface behaves like a USB mouse. In fact, a convenient hardware test is to simply boot the Pi to a desktop and see if you can move the cursor with your trackball or spinner. This can also help you troubleshoot the connections for X and Y inputs. If you have movement, you should be able to configure MAME to use it.

Another test can be performed at the command prompt. Type:`cat /dev/input/mice` and press enter. Now, rotate your spinner or move your trackball. It should produce characters on the screen and move the cursor from side to side on the line. Depending on other devices you have attached, Linux might see more than one USB mouse at the same time. You can determine which one is your spinner or trackball by trying each device individually using `cat /dev/input/mouse0` or `cat /dev/input/mouse1` and so on.

# Configuring AdvanceMAME
Mouse input works in several versions of MAME. For example, can now use **lr-mame2003** for most titles, but if you need to configure multiple inputs or if you are trying to get the best vector game experience, you might be relying on AdvanceMAME. If configured properly, AdvanceMAME offers the most versatility when it comes to trackball and spinner controls. Using the configuration file, You can exert very granular control to override the setup for specific games, or just configure your default settings for all games. This section describes important configuration steps necessary to enable mouse inputs in AdvanceMAME.

## Configuring RAW, PS2 for all possible mouse inputs
Depending on your setup, you might have an external mouse, a spinner, a mouse and a spinner, no mouse and two spinners, one spinner and a trackball, a mouse only during setup, etc.. Linux will see all of these as mouse inputs, but might not see them with the same index. For example, if you boot with an external mouse, that might be detected as mouse0 and your spinner as mouse1, but if you boot the same system without the external mouse attached, everything might ratchet down (spinner becomes mouse0). This can be frustrating, but we can overcome it by mapping multiple inputs together in MAME.

For starters, we need to configure all possible mouse inputs in the configuration file (we will edit the configuration for AdvanceMAME 1.4).

Find these lines in `/opt/retropie/configs/mame-advancemame/advmame-1.4.rc` and update them as shown:
```
device_mouse raw
device_raw_mousedev[0] /dev/input/mouse0
device_raw_mousedev[1] /dev/input/mouse1
device_raw_mousedev[2] /dev/input/mouse2
device_raw_mousedev[3] /dev/input/mouse3
device_raw_mousetype[0] ps2
device_raw_mousetype[1] ps2
device_raw_mousetype[2] ps2
device_raw_mousetype[4] ps2
```
This establishes 4 different mouse inputs which is probably more than most people will need.

## Mapping Specific Controls
The following configurations can depend on your hardware setup. You can make adjustments as needed, especially if you have multiple inputs you are trying to configure. These configurations are also done in `/opt/retropie/configs/mame-advancemame/advmame-1.4.rc`.

### Trackball
Since most trackball games will be emulated in AdvanceMAME using Player1, configure these lines as follows:
```
input_map[p1_trackballx] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]
input_map[p1_trackbally] mouse[0,y] mouse[1,y] mouse[2,y] mouse[3,y]
```
This tells MAME to map the Player 1 Trackball to the X and Y inputs for all four of our possible mouse inputs. We are covering all possibilities here so if the mouse indexes change (maybe you boot up with an external mouse attached and next time you don't) it won't affect the gameplay. Basicially, all attached mouse inputs will map to the game input.

### Spinner
One spinner will send input on either X or Y for a given mouse. Assuming you have yours connected to the X axis of your interface, configure this line:
```
input_map[p1_dialx] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]
```
Here again, we are covering the possibilities. No matter how Linux and MAME are indexing your mouse devices, the x-axis of all four should map to the game.

If it doesn't work, and you know you have functioning inputs (see tests above) you might have your spinner on the y-axis. You could switch the hardware connection or change the input map to
```input_map[p1_dialx] mouse[0,y] mouse[1,y] mouse[2,y] mouse[3,y]```

You might also find that your spinner rotates in the wrong direction. You can fix that too with a minus sign as follows:
```input_map[p1_trackballx] -mouse[0,x] -mouse[1,x] -mouse[2,x] -mouse[3,x]```

There are many possibile combinations if you have more than one input device. Here's an example for two spinners, both connected to the same USB interface, but the Player 2 spins backwards. So. . .
```
input_map[p1_dialx] mouse[0,x]
input_map[p2_dialx] -mouse[0,y]
```
Notice that from MAME's perspective, both DIAL inputs use the x-axis, but we are using two spinners on the same USB interface, so player 1 of our "mouse0" is x and player 2 is on y. As you can see, AdvanceMAME can handle this easily. Also note that we are not mapping mouse1, 2, 3. On this arcade cabinet we have a dedicated trackball on mouse1 and we don't want people to be able to interfere with our game if they touch the trackball while the spinners are in use.

## Other Considerations
Sometimes, a game doesn't use the DIAL input. It uses Paddle. It can be convenient map inputs for the paddel device just in case:
```input_map[p1_paddlex] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]```

It is also possible to configure controls for certain games only. While this is not generally necessary, you do have the option to override defaults you might have configured above by specifying a ROM/ at the beginning of an input line. For example, if Tempest worked just like every other game but for some reason, just that game has the spinner working backwards, you could specify an additional input for that game only:
```tempest/input_map[p1_trackballx] -mouse[0,x] -mouse[1,x] -mouse[2,x] -mouse[3,x]```

## Sensitivity
Each game may require adjustments to the sensitivity. This too can be configured in the .rc file, but it is easier to adjust this within the MAME GUI. Bring up the menu in AdvanceMAME and just the anlog inputs and test as needed. The results will be saved into the .rc file when you exit.

## Poll Rate
Some spinner hardware is designed with high precision. The encoder + optical sensors are capable of extreme sensitivity. However, this can work against you if Linux is not observing the mouse interface fast enough. It can cause a strange negative effect called "backspin". If you have ever watched an old western movie and noticed how a fast turning wagon wheel can appear to spin backwards--that's the same effect caused by a low frame rate during filming. It can be very frustrating to give a quick spin in Tempest only to watch it move backwards in the game until it slows down. One way to overcome this is to tell Linux to increase the poll rate of the mouse interface. You need to edit your `/boot/cmdline.txt` by appending `usbhid.mousepoll=2` to increase the mouse poll rate.

## Driving Games
Don't just limit your spinners to traditional titles. You might not have considered the fact that steering wheels are just big spinners. Driving games like Pole Position are perfectly suited for spinners.

## Unmapping Joysticks
Once you have your spinners working, you might want to remove the joystick controls for some games. MAME pre-configures joystick inputs in lieu of analog controls for some games to make them playable by users without a spinner/trackball. You could ignore this, but it can be annoying if you bump the joystick or if an observer accidentally touches it and affects your game. Simply go into the MAME GUI menu and edit controls for "this game" and remove the joystick inputs.