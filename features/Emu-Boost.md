---
layout: default
title: EmuBoost
parent: Features
nav_order: 4
---

# EmuBoost
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### EmuBoost

EmuBoost is similar to FeedForward in that it changes your stick feel. One way that EmuBoost has been described is a more organic feeling FeedForward.

0.1.0: EmuBoost has one huge advantage to FeedForward. While FeedForward causes issues when paired with Feathered PIDs EmuBoost is quite happy being run with Feathered PIDs. This is something that many racing pilots are appreciative of.

0.2.0+: EmuBoost and FeedForward now work together graciously since we now have a combined PID controller.

0.3.0+: Feed Forward was removed completely.

### How does EmuBoost work?
EmuBoost is a boost to the error used in calculating your pterm and iterm. This means that your moves will be more aggressive when running a high EmuBoost. Small craft like whoops are quite happy running an EmuBoost of almost 1000!

### Boost Limit
The Boost Limit puts a limit on the EmuBoost which prevents the boost from becoming to aggressive and causing oscillations. The lower that the boost limit is the lower that the EmuBoost is allowed to grow to.

### Tuning EmuBoost/Boost Limit
EmuBoost is simply used for stick feel. If you would like a sharper response you can work at increasing your EmuBoost. If you run a large EmuBoost with a small Boost Limit the sticks will be very sharp at the start of movement changes. Stick feel from EmuBoost is a balance of EmuBoost and Boost Limit. An EmuBoost that is high with a Boost Limit that is high can cause oscillations. If EmuBoost is giving you oscillations lowering your Boost Limit will probably remove those oscillations.

Tiny Whoops are usually happy running a EmuBoost of almost 1000 with a Boost Limit of 200 or more. This can really help lock in the sticks on a tiny whoop.

### DBoost
DBoost/Limit is essentially the same, but is a boost to the error used in calculating your dterm.  Defaults of 0 are off.  Enabling this will be a personal preference and tuning may require lower dTerms and feathered-PIDs adjustments.  If feathered-PID are <= 70, DBoost may induce dTerm kick or jello.

***@ehitaja & @3dracingman Tip (0.2.0+):***
```
set feedforward_transition = 70
set emu_boost = 155
set emu_boost_limit = 30
set emu_boost_yaw = 330
set emu_boost_limit_yaw = 83
set f_pitch = 30
set f_roll = 30
set f_yaw = 20
```

However, many @EmuTestBandits were enjoying a prior recommendation of:
```
set emu_boost = 90
set emu_boost_limit = 90
set emu_boost_yaw = 40
set emu_boost_limit_yaw = 40
set f_pitch = 35
set f_roll = 35
set f_yaw = 35
```

***@nerdCopter Tip (0.2.0+):*** As a less experienced freestyle pilot, I find high FF/Boost values a bit unbridled. Using an X-Lite controller, I prefer low RC-Rates in conjunction with Expo.  Having higher FF/Boost values seems to unsettle this and produce too quick of a response when moving sticks off center.  I prefer a smooth and subtle change.  For me, higher values also make it easier to overshoot my end of roll/flip target.  So for now I'm choosing Low FF/Boost values.  Also notice that many popular presets have zero FF/Boosts.