---
layout: default
title: Installation
parent: Getting Started
nav_order: 1
---

# Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to install EmuFlight firmware on your FC:

Using <span class="fs-2">[EmuFlight Configurator](https://github.com/emuflight/EmuConfigurator/releases){: .btn .btn-blue }</span>, select the Firmware Flasher tab and select what firmware to flash in one of two different ways, online or local firmware.
  1. Load online firmware.
Select Target and Version in the upper left corner. Press "Load Firmware [Online]", lower right part of the screen.
  2. Load local firmware.
 Press the "Load firmware [Local]" button, you can now browse to the folder you have the local EmuFlight firmware file. Select the correct firmware hex-file matching your Flight Controller.

![](/assets/images/emuconfig.png)

It is recommended to always save `diff all` files of your flight controller settings, especially when upgrading between versions.  It is recommended to "Erase Flash" between major versions to avoid incompatible parameter values and to avoid CLI lock-up during the initial auto-complete cache building.

Choose your firmware, then press "Flash Firmware".  The Configuration tool should now erase the target and flash the selected firmware to your Flight controller. All this assumes you have the correct drivers etc setup correctly, read further on for details.

Pre-Release firmware may be found by enabling `Show unstable releases` and selecting `Release And Release Candidate`.

![](/assets/images/show_unstable.png)

## Helio-Spring/Strix-F10/Mode2-Flux

A extra few steps are needed in the case of the Helio Spring and Strix F10 boards after flashing the firmware in the steps above.

1. Download The <span class="fs-2">[IMU-F Updater Tool](https://github.com/emuflight/imu-f/releases/download/209/HELIO-IMU-F-Updater.zip){: .btn .btn-blue }</span> and extract the contents of the zip file to your computer.
2. Open the .exe file
3. Type or select COM port and hit Connect, you should be presented with information on the board and IMU-F version.

![](https://github.com/emuflight/EmuFlight-Butter-Varient/blob/master/docs/assets/images/imuf_flashing_3.png)

4. Download an appropriate <span class="fs-2">[IMU-F firmware](https://github.com/emuflight/imu-f/releases){: .btn .btn-blue }</span> then hit Select firmware.  Note: Development versions up to 0.2.31 inclusive can use any IMUF up to 224 inclusive.  Dev 0.2.32 and above including soon to be released 0.3.0 will need a newer IMUF for the new `sharpness` variable.

![](https://github.com/emuflight/EmuFlight-Butter-Varient/blob/master/docs/assets/images/imuf_flashing_4.png)

5. Leave 'Original HELIO Firmware' unchecked and hit Flash Firmware. Note: Older HelioRC® provided IMUF firmware requires the checkbox enabled; whereas EmuFlight™ provided IMUF firmware require the checkbox disabled.  If for any reason you flash in the wrong mode, you must re-plug and power your FC and wait a full 5 minutes to re-flash it properly. Do not worry, it is not bricked; just wait for the timeout.

![](https://github.com/emuflight/EmuFlight-Butter-Varient/blob/master/docs/assets/images/imuf_flashing_5.png)

6. You should be presented with the status text on the left updating. Wait until this is finished and a prompt will appear stating that you have been disconnected from the port. Hit OK and the Updater will close automatically.

![](https://github.com/emuflight/EmuFlight-Butter-Varient/blob/master/docs/assets/images/imuf_flashing_6.png)

**Congratulations! You have updated your IMU-F firmware**

## Troubleshooting

**If you are having trouble connecting to your flight controller, please take a look at this video:**

[![](https://img.youtube.com/vi/m4ygG6Y5zXI/0.jpg)](https://www.youtube.com/watch?v=m4ygG6Y5zXI)

_In Progress_