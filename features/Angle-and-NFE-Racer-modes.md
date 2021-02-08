---
layout: default
title: Angle and NFE Racer modes
parent: Features
nav_order: 1
---

# Angle-Mode and NFE-Racer Mode
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### Angle-Mode and NFE-Racer Mode

ONLY IN 0.3.0 AND LATER

Angle mode in EmuFlight has taken a lot of influence from SilverWare angle code. As such EmuFlight has advanced angle mode features only found in EmuFlight and SilverWare. 

### Angle PIDs

Angle mode has high and low PIDs. This referrers to high error and low error, aka high error is from crashes or very, very abrupt stick movements. The reason why there are low and high PIDs is simple, it removes most of issues that happen when crashing or bumping into things in Angle mode. This means you are far less likely to get sucked against a wall or get thrown off at a weird angle.

Low angle PIDs are your primary "flight" PIDs. As such angle P is equivalent to angle strength, and angle D is an actual D on your angle. EmuFlight also has a FeedForward for angle mode (currently the only FeedForward in EmuFlight). This will make the angle feel more reactive to your movements, set it to high and you will overshoot and it will not feel right. If you are crashing and constantly getting sucked against a wall or having other issues try lowering the high angle PID settings. Setting that lower will have less leveling effect at a high angle error, which happens as your whoop tries to suck into a wall.

Angle expo adds an exponential curve to your sticks while in angle mode. Your rates have no effect (except for yaw) while you are in angle mode. Angle expo adds a curve which keeps angle from being directly linear based on your stick deflection. This can make it easier to run a higher max angle without it feeling to jittery.

### NFE-Racer Mode

NFE-Racer mode is equivalent of Angle-Mode on roll and Acro-Mode on pitch.
You can enable NFE-Racer mode in the PIDs tab or type "set nfe_racermode = ON" in the CLI.

Defaults:
```
set nfe_racermode = OFF
set p_angle_low = 100
set d_angle_low = 10
set p_angle_high = 35
set d_angle_high = 1
set f_angle = 40
set angle_expo = 10
```

### NFE on switch
0.3.3 Adds NFE on an aux-mode switch rather than profile option.

### Mix Roll and Yaw
0.3.3 Adds the ability to mix roll and yaw -- a.k.a "Dual Axis Steering".  Mix roll stick into yaw, or yaw stick into roll. This is something usually done on the radio, but our slightly different method vs the radio method seems to have benefit especially for crash recovery. It is really good for top angle whoop racing pilots.

Independent but useful, also adds "roll pitch magnitude expo" which adds an expo to your roll and pitch when the magnitude of pitch and roll are greater than 1.0f. Then it applies extra expo to these sticks and reduces the max value of both pitch and roll. 

\* full-release 0.3.3 fixes the naming scheme since there has been feedback and confusion on the pre-release.

release 0.3.3:
```
# get das
das_yaw_with_roll_input = 0
rateprofile 0
Allowed range: 0 - 100

das_roll_with_yaw_input = 0
rateprofile 0
Allowed range: 0 - 100
```

pre-release 0.3.3:
```
add_roll_in_yaw = 0
rateprofile 0
Allowed range: 0 - 100

add_yaw_in_roll = 0
rateprofile 0
Allowed range: 0 - 100
```

both:
```
roll_pitch_mag_expo = 0
rateprofile 0
Allowed range: 0 - 250
```
