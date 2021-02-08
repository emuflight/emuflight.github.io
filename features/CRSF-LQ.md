---
layout: default
title: CRSF LQ
parent: Features
nav_order: 2
---

# CRSF LQ
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## TBS Crossfire LQ in OSD Support (0.3.2+)

* Enable RSSI/LQ OSD in Configurator.
* Transmitter should be setup for LQ (default).
* Set OSD Widget style in CLI: `set osd_lq_format =` [`SCALE`,`TBS`,`MODE`,`FREQ`,`SIMPLE`].
* 0.3.2 defaults to `TBS`, while 0.3.3+ defaults to `SCALE`.

### Analog:
* AUX channel is _not_ required for OSD LQ Display (with modern TX firmware). EmuFlight 0.3.2+ will just "see" the LQ telemetry.
* If your RSI/LQ continuously blinks, then enable RSSI_ADC in Configurator.

### DJI:

DJI does not currently support scales that distinguish between 150hz or 50hz modes but the most relevant LQ information is still available via OSD.  In order to **set this up** you still need to:
* Map LQ to a channel on your TBS Crossfire RX (on each RX you want to setup)
	* _Note: You may also map RSSI or RSSI/LQ to that channel, but for these purposes you can only choose one and LQ should be the most useful for most pilots._
* On the receiver tab, enable RSSI Channel on the appropriate AUX channel i.e. the channel you mapped "LQ" to on your Crossfire RX -4. So if you chose channel 8, you would selected AUX4.
* In the OSD tab you have to enable "RSSI/LQ" value
**Appearance in the OSD:**
	* Example OSD Widget: `100`
	* RFMD2 i.e. 150hz mode:  `99`
	* RFMD1 i.e. 50hz mode:  `0-99` *notice that this overlaps with RFMD2.
	* RFMD0 i.e. 4hz mode:  N/A
	* **TBS defined “turn around” criteria**:  `70`

### Crossfire LQ can be displayed different styles in OSD:

#### SCALE (Only in 0.3.3+; _default_ in 0.3.3)
* CLI command: `set osd_lq_format = SCALE`
* Example OSD Widget: `LQ 300`
* RFMD2 i.e. 150hz mode: `LQ 170-300`
* RFMD1 i.e. 50hz mode: `LQ 0-100`
* RFMD0 i.e. 4hz mode: `LQ 0-100` **note:** you will never see these values unless you explicitly setup your system for them. They're not really applicable to flying quads.
* **TBS defined "turn around" criteria**: `LQ 70` where 70 scaled-out is 262

#### TBS (_default_ in 0.3.2)
* CLI command: `set osd_lq_format = TBS`
* Example OSD Widget: `LQ 300`
* RFMD2 i.e. 150hz mode: `LQ 200-300`
* RFMD1 i.e. 50hz mode: `LQ 0-100`
* RFMD0 i.e. 4hz mode: `LQ 0-100` **note:** you will never see these values unless you explicitly setup your system for them. They're not really applicable to flying quads.
* **TBS defined "turn around" criteria**: `LQ 70` where 70x3 is 210.

#### MODE
* CLI command: `set osd_lq_format = MODE`
* Example OSD Widget: `2:100`
* RFMD2 i.e. 150hz mode: `2:0-2:100`
* RFMD1 i.e. 50hz mode: `1:0-1:100`
* RFMD0 i.e. 4hz mode: `0:0-0:100` **note:** you will never see these values unless you explicitly setup your system for them. They're not really applicable to flying quads.
* **TBS defined "turn around" criteria**: `1:70`

#### FREQ
* CLI command: `set osd_lq_format = FREQ`
* Example OSD Widget: `150HZ:100`
* RFMD2 i.e. 150hz mode: `150HZ:0 - 150HZ:100`
* RFMD1 i.e. 50hz mode: `50HZ:0 - 50HZ:100`
* RFMD0 i.e. 4hz mode: `4HZ:0 - 4HZ:100` **note:** you will never see these values unless you explicitly setup your system for them. They're not really applicable to flying quads.
* **TBS defined "turn around" criteria**: `50HZ:70`

#### SIMPLE (only in 0.3.3+)
* CLI command: `set osd_lq_format = SIMPLE`
* Example OSD Widget: `LQ 100`
* RFMD2 i.e. 150hz mode: `LQ0-100`
* RFMD1 i.e. 50hz mode: `LQ 0-100`
* RFMD0 i.e. 4hz mode: `LQ 0-100` **note:** you will never see these values unless you explicitly setup your system for them. They're not really applicable to flying quads.
* **TBS defined "turn around" criteria**: `LQ 70`

### Options
* Blink warning is configurable with CLI `set osd_lq_alarm`. Default is `70` (where 3x70=`210`). 
* CLI can enable SNR (Signal to Noise Ratio) and TX Power OSD widgets.
* CLI `get lq` & `get crsf` for options.

### Notes
* Configurator is not yet updated, but Signal-Noise-Ratio and TX-Power can be enabled/positioned with `Unknown 1` & `Unknown 2`.
* Signal-Noise-Ratio and TX-Power can also be enabled in the OSD.
* Older EmuFlight (<=0.3.1) does not support LQ OSD Display.


***

@Alf-Dee Tip:
So, I finally managed to understand how to set **Crossfire LQ  in the DJI OSD** on emu 0.3.2 and Crossfire 4.x (it should work also on EMU 0.3.x, but for some reason I had to reconfigure it. So if you can't see anything, reset all parameters and restart).

* If you have crossfire firmware prior to 4.x (4 still in beta) you need to manually configure on XF rx channel 8 to output LQ (See picture of my radio. Instead of Channel 12 you should see Channel 8). If you have crossfire firmware 4.x or newer XF rx outputs LQ on channel 8 by default freeing up channel 12 at your disposal.
* In the Emu 0.3.4 configurator disable RSSI_ADC in configuration tab. (This seems to work only on analogue VTX).
* In the Receiver tab enable RSSI Channel on AUX 4. (this should work with both CX 3.x and 4.x).
* In the OSD tab you have to enable RSSI/LQ value
* If it still don't work, try forcing the LQ mode manually in the CLI
set osd_lq_format = tbs and then type save
* Also, it isn't necessary but I always set in the Failsafe tab the AUX 4 Line to "Set" 1000. If you leave it with the Hold flag you won't see the LQ to 0 if you shut down your transmitter
* LQ will be displayed in DJI osd between 0 and 100. In my tests I never saw it dropping below 90 at 25mw power output, so I guess you should turn around and come back if you drop below 70-75

Thank you @CesiumSalami for help and feedback of this Documentation.


***
### Visuals
* LQ Widget Styles: https://youtu.be/VrY6zT1yY-s
* LQ, SNR, TX-Power, & RSSI dBm widget config via OSD: https://youtu.be/CVroHVWUAcQ
* Same, plus LQ Style config via OSD [not released]: https://youtu.be/7p1SK9HZSWk
