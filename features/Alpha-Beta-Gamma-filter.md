---
layout: default
title: Alpha Beta Gamma filter
parent: Features
nav_order: 15
---

# Alpha Beta Gamma filter

ABG (αβγ) - [https://www.kalmanfilter.net/alphabeta.html](https://www.kalmanfilter.net/alphabeta.html)

0.4.0+ adds Alpha-Beta-Gamma filter on dTerm or Gyro. Default is off.

on dTerm:
* `dterm_abg_alpha` (OSD: DTERM ABG ALPHA) Range 0-1000, default 0 (ABG dTerm off)
* `dterm_abg_boost` (OSD: DTERM ABG BOOST) Range 0-2000, default 275
* `dterm_abg_half_life` (OSD: DTERM ABG HL) Range 0-10000, default 50

on Gyro:
* `gyro_abg_alpha` (OSD: GYRO ABG ALPHA) Range 0-1000, default 0 (ABG Gyro off)
* `gyro_abg_boost` (OSD: GYRO ABG BOOST) Range 0-2000, default 275
* `gyro_abg_half_life` (OSD: GYRO ABG HL) Range 0-10000, default 50

From testing Alpha Beta Gamma filter should only be used in conjunction with a lowpass filter. Results of the lowpass Alpha Beta Gamma filter combo do show better results than just a lowpass filter on its own, and is thus still worth persuing. 

ABG is more of a movement promotor than it is a filter. It can be used to track motion with near zero delay response, but doesn't require a simulated system model to do it. Blackbox logs show that the lower you set the Alpha value, the lower the noise floor but you get a stronger peak on movement band (as it promotes movement). It should be noted that any existing tuning oscillations typically are amplified under the alpha value.
The lower the Alpha value, the more the output is filtered. Disable by setting Alpha value to 0.
ABG boost will decrease ABG latency, but higher values may feel unnatural.
ABG has memory and it decays based on abg halflife, where the value is in ms.
