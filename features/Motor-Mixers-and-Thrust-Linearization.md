---
layout: default
title: Motor Mixers and Thrust Linearization
parent: Features
nav_order: 9
---

# Motor Mixers and Thrust Linearization
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Motor Mixers and  Thrust Linearization

### 0.4.0+
The new mixers and linearizations are independent functions but may be used together to provide a preferred fly-style. Code and ideas from Tyler Corleone and QuickFlash.

### Motor Output Mixer - Options for the controller's motor output.  New smooth variants change how the axes are mixed with throttle.
- `LEGACY` is the mixer we have always had. (Note: for 100% legacy-mode, `linear_throttle` should be `OFF` and `linear_thrust_high_output` should be `0`; However, pilots are welcome to use both Thrust-Linearization and Throttle-Linearization.)
- `SMOOTH` is a simple variant that applies smoother transitions to avoid mixer-output clipping.
- `2PASS` is a SMOOTH variant that mixes yaw and roll/pitch separately in order to try to guarantee thrust linearity for roll and pitch and motor output linearity (almost RPM linearity) for yaw.
- `mixer_laziness` ON/OFF. When ON, requires Thrust-Linearization values configured (`>0`). Both SMOOTH and 2PASS can use an option called "laziness" that enables a smarter "clipping prevention" strategy, that is called lazy because it adds only the minimum required amount of offset to remain in the [0, 1] for each "motor group" (that is a group of opposite motors that can actually work in conjunction in order to obtain a certain amount of roll/pitch) instead of applying the biggest needed amount. In this way we avoid to add/increase the total thrust when not needed, obtaining a better "throttle authority".
- `mixer_yaw_throttle_comp` compensate throttle for increased motor output during aggressive yaw maneuvers.  This option applies only to `2PASS`.  `LEGACY` does not suffer from the issue. `SMOOTH` still suffers from the issue.

```
# get mixer

mixer_impl = 2PASS
Allowed values: LEGACY, SMOOTH, 2PASS
Default value: 2PASS

mixer_laziness = ON
Allowed values: OFF, ON
Default value: OFF

mixer_yaw_throttle_comp = ON
Allowed values: OFF, ON
```

### Thrust Linearization - Compensation for inherent non-linearity of thrust and rpm of motor output.
- Two settings: `linear_thrust_low_output` for low motor output (low RPM) and `linear_thrust_high_output` for high motor output (high RPM). Use this tool to understand what you need to set (65/30 are good starting points for low and high output) https://www.desmos.com/calculator/ofaiocun0b
- Both values need to be != 0 (not zero) for TL being applied.
- `linear_throttle` gives you a linear throttle/thrust feeling. The hovering level will be lower (e.g. what before was 30% now could be 20%). This means that you need to be used to this before you can appreciate its advantages (more room on the upper part of the throttle)
- [TPA](https://github.com/emuflight/EmuFlight/wiki/TPA) is automatically disabled when TL is enabled because it already solves high throttle issues.


```
# get linear

linear_thrust_low_output = 65
Allowed range: 0 - 100

linear_thrust_high_output = 30
Allowed range: 0 - 100
Default value: 0

linear_throttle = ON
Allowed values: OFF, ON
Default value: OFF
```

For more information, please see all notes, graphs and discussions in the Pull Request: https://github.com/emuflight/EmuFlight/pull/398

### Suggested starting values for Thrust Linearization: 
* When over-propping, lower these values some points. 
* When under-propping, raise these values some points. 
* Such will affect `linear_thrust_low_output` more.  Tune values as needed based on P-Term overshoot or undershoot.

| Make/Model  | Size  | TL Low  | TL High |
|---|---|:---:|:---:|
| NewBeeDrone Brushed Gold | 19700kv | 70 | 45 |
| NewBeeDrone Brushed Unicorn | 25500kv | 70 | 45 |
| Generic  | 1102 | 45 | 30 |
| DongXingWei | 1103 8000kv | 40 | 25 |
| Generic | 1105 | 75 | 35 |
| Amax | 1105 5800kv-GF2540 | 82 | 49 |
| EMAX | 1106 6000kv-GF3035 | 85 | 10 |
| T-motor F15 | 1106 6000kv HQ2525 | 90 | 45 |
| Tachyon | 1108 5000kv GF3035 | 95 | 42 |
| FPVCycle | 1202 6300kv HQ3x2 | 65 | 10 |
| iFlightXing | 1202 8000kv | 75 | 35 |
| iFlightXing | 1204 4500kv GF3025 | 92 | 56 |
| iFlightXing | 1206 6500kv GF2540 |80 | 80 |
| FPVCycle | 1303 5200kv HQ3x2 | 94 | 34 |
| EMAX | 1306 4000kv GF3035 | 93 | 87 |
| BetaFPV | 1404 3800kv GF3025 | 95 | 95 |
| HypeTrainBRAT | 1407 4140kv HQ2525 | 95 | 75 |
| BetaFPV | 1505 3600kv GF3025 | 95 | 95 |
| BetaFPV | 1805 1550kv 6S | 95 | 76 |
| BetaFPV | 2004 1700kv 6S | 69 | 90 |
| ZoeFPV | 2010 | 60 | 25 |
| Proton X | 2204 | 50 | 0 |
| SunnySky | 2204 | 50 | 0 |
| RCX V2 | 2205 | 50 | 15 |
| RCINPower | 2205 | 60 | 15 |
| ZoeFPV | 2205 | 60 | 5 |
| iFlight Xing | 2206 | 60 | 30 |
| T-Motor Blackbird | 2207 | 60 | 15 |
| Pyrodrone Hyperlite | 2207.5 | 60 | 25 |
| Flywoo | 2207.5 1860kv | 40 | 20 |
| FlashHobby Arthur | 2207.5 1900kv | 60 | 30 |
| Pyrodrone Hyperlite | 2208.5 | 55 | 25 |
| AmaxInno | 2305 | 63 | 25 |
| NewBeeDrone Smoov | 2306 2400kv | 60 | 15 |
| LeDrib | 2306 | 65 | 15 |
| AmaxInno | 2306 | 65 | 40 |
| iFlight Xing | 2306 | 75 | 30 |
| NewBeedrone Flow | 2306.5 | 70 | 30 |
| T-motor BMS | 2306.5 2000kv | 60 | 29 |
| Bardwell | 2407 | 65 | 30 |
| HGLRC FD | 2408 | 70 | 25 |
| T-Motor F80 | 2408 | 75 | 45 |
| T-Motor F90 | 2806.5 | 70 | 60 |
| Emax Eco II | 2807 | 75 | 95 |

\* Credit to Ryan Harrel ([MiniQuad Bench Test](https://www.miniquadtestbench.com/motor-explorer.html)), Ethan Bayer ([Micro Motor Test Lab](https://www.facebook.com/groups/MicroMotorTestLab/)) for the thrust curve data from which these values were derived. Thanks to DrSchnickistein and EmuTestBandits for value recommendations.

@nerdCopter Tip: Recommend LEGACY or SMOOTH for cinematic aircraft.  Recommend LEGACY or 2PASS+Laziness for racing and freestyle.  Recommend tuned Thrust-Linearization (Use the table for deducing good values and tune as needed).  Throttle-Linearization will depend on the aircraft and pilot preference as the throttle hover-point may be reduced too much on some craft.
