---
layout: default
title: Installation
parent: Getting Started
nav_order: 2
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

![EmuConfigurator](/assets/images/emuconfig.png)

It is recommended to always save `diff all` files of your flight controller settings, especially when upgrading between versions.  It is recommended to "Erase Flash" between major versions to avoid incompatible parameter values and to avoid CLI lock-up during the initial auto-complete cache building.

Choose your firmware, then press "Flash Firmware".  The Configuration tool should now erase the target and flash the selected firmware to your Flight controller. All this assumes you have the correct drivers etc setup correctly, read further on for details.

Pre-Release firmware may be found by enabling `Show unstable releases` and selecting `Release And Release Candidate`.

![Show Unstable Releases](/assets/images/show_unstable.png)

## Helio-Spring/Strix-F10/Mode2-Flux

To flash the IMUF chip on Helio Spring and Strix F10 boards, use the new [IMUF-Flasher tool](https://github.com/emuflight/Nemesis/releases/tag/imuf-flasher-0.1.0).  You may also use the [old method](https://github.com/emuflight/EmuFlight/wiki/Installing-EmuFlight#helio-springstrix-f10mode2-flux).

## Troubleshooting

**If you are having trouble connecting to your flight controller, please take a look at this video:**

[![](https://img.youtube.com/vi/m4ygG6Y5zXI/0.jpg)](https://www.youtube.com/watch?v=m4ygG6Y5zXI)

_In Progress_
