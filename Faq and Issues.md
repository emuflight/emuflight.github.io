---
layout: default
title: FAQ and Issues
nav_order: 5
---

# FAQ and Issues
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
# Origins of EmuFlight
EmuFlight was created the summer of 2019 when Marinus decided to start working on updating the IMUF code which was opensourced by HelioRC. After creating a few updates to the IMUF a version of the IMUF was put into a fork of Butterflight. The project had no name for some time until a poll was created and voted on by users of this code. The name that won the vote was EmuFlight and the iconic blue bird was born! Since then EmuFlight has added much more to its code than just the IMUF filter. 

***
# Are you Helio/ButterFlight?
Helio is dead. ButterFlight is dead. EmuFlight is not Butterflight or Helio. In fact EmuFlight is a new team of developers that include none of the old Helio or Butterflight devlopers. We do not want to be thought of as Helio or Butterflight. We do not want to cause drama in the drone community. We are only here to help you have a better time flying your quadcopter. That being said if you were a fan of Helio or Butterflight then you will probably be a fan of EmuFlight. 

***
# 32k Gyro and PID Loops
EmuFlight is the last opensource software to continue to support 32k. Because of the feelings that many users have around 32k, it is not on by default. However many of our users prefer 32k, while others seem to prefer 4k. Many of the problems that 32k has seen in the past are solved by better filtering that is found in EmuFlight. If your wondering if 32k is worth it give it a try and come up with your own opinion. Another fun thing to play with is turning the gyro to experimental mode which almost completely removes the built in gyro lowpass filter (this is what FlightOne does).

**Skylion Tip:** If you want to run full 32k/32k on most flight controllers you will need to overclock to 240mhz on f4 or f7 flight controllers in order to get your cpu% down to a reasonable level. In my experience most people will not notice the difference between 16k/16k and 32k/32k, unless you are pushing your quad to the absolute limit. If you would like to try 32k/16k you'll only have to overclock to 216mhz on f4 and no overclock on f7, 16k/16k on f4 might want to overclock to 192mhz but shouldn't be totally necessary. 

***
# DJI

DJI compatibility has NOT been focused on.

* ***DJI devices may bypass USB arming block, DO NOT attempt arming DJI component based quads while plugged into Configurator, especially with propellers mounted. Always Props-off! This is always how things should be done, but be warned that DJI will cause arming to be allowed in the Configurator! Use a smoke-stopper for added protection.***

| UI  | Note  |
|---|---|
|PID PROF| working|
|| |
|PID >| |
|ROLL P| working|
|ROLL I| working|
|ROLL D| working|
|ROLL F| LOW ANGLE ERROR D|
|PITCH P| working|
|PITCH I| working|
|PITCH D| working|
|PITCH F| no effect|
|YAW P| working|
|YAW I| working|
|YAW D| working|
|YAW F| HIGH ANGLE ERROR D|
|| |
|MISC PP >| |
|FF TRANS| will not change|
|ANGLE STR| will not change|
|HORZN STR| will not change|
|HORZN TAS| will not change|
|AG GAIN| will not change|
|AG THR| will not change|
|THR BOOST| working|
|| |
|FILT PP >| |
|DTERM LPF| IN OSD starts at 25600 and when setting, it sets very large numbers in Matrix filter notch min, D |Term lowpass cutoff 1 (21870 and 63076 when set to 25590)|
|DTERM LPF2| Reading 0 instead of setting in config which is 250. setting it in osd has no efffect, but it |allows change in the osd|
|DTERM NF| Reading 0 and setting it has no effect in cli or config|
|DTERM NFC0| setting between 0,1,2,3,4 Gyro Notch Filter 2 Center Frequency [hz] moves to 0 (disable in gui), |256, 512, 768, 1024|
|YAW LPF| IN OSD 25600 and when setting, affects dterm_lowpass_hz_pitch and dterm_lowpass_hz_yaw (large negative  |number and 99)|
|| |
|RATE PROF>| working|
|RATE>| |
|RC, SUPER, EXPO| working|
|THR MID| working|
|THR EXPO| working|
|THRPID ATT| working (TPA P)|
|TPA BRKPT| working (TPA Breakpoint)|
|| |
|"FLIT" GLB > (dji typo)| |
|GYRO LPF| 26880 at start, and when setting, it affects gyro_lowpass_hz_pitch and gyro_lowpass_hz_yaw in cli |(-7821, and 104)|
|GYRO LPF2| 0,1,2,4 in osd. no difference in config or diff|
|GYRO NF1 | no effect, setting not saved|
|GYRO NF1C | OSD Does not allow change|
|GYRO NF2| setting numbrs 0,1,2,3 does 256, 512, 768 on gyro_notch2_cutoff. also affects dterm_lowpass_hz_yaw ?|
|GYRO NF2C | no effect, setting not saved|
|| |
|COPY PID PROFILE| working|
|COPY RATE PROFILE|| working|

***
# VTX PINIO User1

`resource PINIO 1 <pin>`
& 
`set pinio_box = 40,-1,-1,-1` in most cases

Please see https://github.com/betaflight/betaflight/wiki/Pinio-and-PinioBox

***
# VTX Power on switch

## VTX Power on an aux-mode switch

New in 0.3.3+, Adds an option to change vtx power with an aux channel.
 More info on usage: https://github.com/betaflight/betaflight/wiki/VTX-CLI-Settings

Example cli settings:

6-Position example on AUX6:
```
vtx 0 7 5 1 0 900 1100
vtx 1 7 5 2 0 1100 1300
vtx 2 7 5 3 0 1300 1500
vtx 3 7 5 4 0 1500 1700
vtx 4 7 5 6 0 1700 1900
vtx 5 7 5 8 0 1900 2100
```

2-Position example on AUX7:
```
vtx 6 6 0 0 1 900 1200
vtx 7 6 0 0 2 1800 2100
```

The above 2-Position example uses AUX7 ( channels are zero indexed, change to whatever channel number you have set up on the radio minus 1) and will switch between power modes 1 and 2 when aux-mode switch is within related ranges.

Easiest way to tell is to enable the VTX OSD element. You will see power change in the OSD. Make sure you have armed the quad once (to make sure you are not in lowpower disarm mode)
Note:

For Smart audio, the power levels are hardcoded in EmuFlight 0.X.Y as:
* 1: 25mw
* 2: 200mw
* 3: 800mw

***Make sure not to use more than the vtx allows.***

[Unsure if this applies to Tramp; power-levels are preset in the vtx itself.]

***
# Beeper Fixes

## NONSTOP BEEPER

Quick fix for beeper issues some users have experienced. The issue comes with some bad beeper defaults brought from butterflight. Simply typing this into the cli should remove the last few beeper presets you may not want that are probably causing your beeper to beep nonstop. 

```python
set beeper GPS_STATUS = off
set beeper CRASH FLIP = off
set beeper CAM_CONNECTION_OPEN = off
set beeper CAM_CONNECTION_CLOSED = off
set beeper RC_SMOOTHING_INIT_FAIL = off
```

## NO BEEPER

If your beeper just does not seem to be working at all then for the time being this code put into your cli should turn on your beepers.

```python
beacon RX_LOST
beacon RX_SET
```

***
# OSD_font_logo

Please upload fonts to your flight-controllers.

Please note that some flight controllers require battery power to successfully save fonts.

v2 fonts are supported with 0.2.22-RC2, dev-versions ≥0.2.35, and 0.3.X using [EmuConfigurator](https://github.com/emuflight/EmuConfigurator/releases) 0.2.12-RC2 or newer.

v1 fonts are mostly fixed in EmuConfigurator 0.2.16 and above with some caveats. Crosshair works.

Feel free to use this Logo to build your own fonts.

![EmuFlight-OSD.png](/assets/images/EmuFlight-OSD.png)

***
# GPS Lock Bypass

Bypassing the satellite lock requirement may be a safety issue.  We do _not_ recommend such; However, it is frequently asked if such is possible.  This is technically possible with `set gps_rescue_min_sats = 0`.  Default is `8`.

@glossy_fpv Tip: Just remember that if you hit return to home or failsafe and you took off with 0 sats you will not return home. Use min 6 sats to return home.

Do you want failsafe-drop and GPS-rescue on a switch?

@daveskybiker tip: Min sats 0, gps rescue on a switch, failsafe drop. Just get 6 min sats before you arm if you want gps rescue.

***
# Building Targets

Although building is possible on any platform, here is the Debian/Ubuntu method.

one time:
```
sudo apt install git build-essential
git clone https://github.com/emuflight/EmuFlight.git
```

build:
```
cd EmuFlight

#on occasion when arm_sdk changes:
make arm_sdk_install --always-make

#build targets (single, list, or all):
make HELIOSPRING FOXEERF405 MATEKF722

# make all --keep-going
```

Note: this works with `git checkout [branch or commit]` also.

# Artwork

## EmuFlight Artwork
All artwork is original works by and courtesy of  [@kumokraft](https://www.youtube.com/user/kumokraft/videos){: .btn .btn-blue }

[![](/assets/artwork/EMUFLIGHT-LOGO_YT-Header-01-01.png)](/assets/artwork/EMUFLIGHT-LOGO_YT-Header-01-01.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_YT-Backdrop-02.png)](/assets/artwork/EMUFLIGHT-LOGO_YT-Backdrop-02.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_YT-Backdrop-01.png)](./artwork/EMUFLIGHT-LOGO_YT-Backdrop-01.png#thumbnail)
[![](/assets/artwork/EMUFLIGHT-LOGO_-03_BlueLogoTransBack.png)](/assets/artwork/EMUFLIGHT-LOGO_-03_BlueLogoTransBack.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_-02_WhiteLogoTransBack.png)](/assets/artwork/EMUFLIGHT-LOGO_-02_WhiteLogoTransBack.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_-02_WhiteLogoTransBack.png)](/assets/artwork/EMUFLIGHT-LOGO_-01_SolidBlue.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_-05SolidWhiteCircleLogoTransBack.png)](/assets/artwork/EMUFLIGHT-LOGO_-05SolidWhiteCircleLogoTransBack.png)
[![](/assets/artwork/EMUFLIGHT-LOGO_-04_SolidBlueCircleLogoTransBack.png)](/assets/artwork/EMUFLIGHT-LOGO_-04_SolidBlueCircleLogoTransBack.png)