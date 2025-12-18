---
layout: default
title: Flashing RetroGo
nav_order: 4
---

Flashing Retro-Go
=================

Once the mod installed in the handeld console, it is time to flash the ESP32 system
with a compatible Retro-Go version that has been specifically developed for this mod.
Retro-Go is a wonderful ESP32 retro-gaming platform using various emulators to run
old games on emulated consoles. It is easy to deploy and the [project website](https://github.com/ducalex/retro-go)
does explain how to manage games on the device's SD card and much more. 

Download our custom Retro-Go image
----------------------------------

We provide a prebuilt image for this TsingTao mod that can be downloaded from [our release page](https://github.com/virtualabs/retro-go/releases/download/tsingtao-v1.0/tsingtao-retrogo-v1.img).
This image has been specifically built for this mod and features some hardcoded configuration
and custom drivers to correctly interface with the console screen and our dedicated daughter boards.

You can also follow [the build instructions](https://github.com/virtualabs/retro-go/blob/master/BUILDING.md)
to compile it from source, and flash the generated image into the mod system.

Flash your ESP32
----------------

*Important: do not insert any micro SD card in the console's SD card holder !*

First, you need to install `esptool` on your system, as it is required to successfully flash
the TsingTao Retro-Go image. It should be available in most Linux distributions as a standard
package, if not you can install it by following [Espressif's setup guide](https://docs.espressif.com/projects/esptool/en/latest/esp32/).

Then, connect your modded console to your computer using a USB cable. Make sure the console is powered
on (power switch facing `ON`), and issue the following command (replace ``tsingtao_*.img`` with the
filename of the image downloaded in the previous step):

```shell
$ esptool.py write_flash --flash_size detect 0x0 tsingtao-retrogo-v*.img
```

This operation can take minutes to complete. Once done, switch off the console.

First boot
----------

Format your micro SD card in FAT32 and insert it into the micro SD card holder. Then switch on
the console, it will fill the micro SD card with the required folders for ROMS and themes at
first boot.

Switch off the console again, eject the micro SD card and copy ROM files to the corresponding
folders and insert it again into the handeld. Switch it on, and you should see your games in
the list of games of the console they were designed to run on.


Frequently Asked Questions
==========================

TsingTao is not detected when connected to my computer, did I do anything wrong ?
---------------------------------------------------------------------------------

First, make sure the USB cable used to connect the console to your computer is not a charge-only
USB cable. Then, check the power switch has correctly been placed when reassembling the console:
it could be misplaced and tit won't switch the console on. If any of this worked, check your
solder job and make sure the mod's `DM` and `DP` pads are correctly connected to the type A USB
plug.




