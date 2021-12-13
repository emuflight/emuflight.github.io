---
layout: default
title: Alpha Beta Gamma filter
parent: Features
nav_order: 15
---

## ABG (αβγ) - https://www.kalmanfilter.net/alphabeta.html

### 0.4.0+
* Adds Alpha-Beta-Gamma filter on dTerm or Gyro. Default is OFF.
* Used to gain cleaner or more fine-tuned filtering.
* One can achieve a great tune without ABG.  ABG is not a requirement.
* Sweet-Spot seems to be 300 - 600 range for ABG alpha.
* As ABG is enabled, P's and D's may likely need decreasing.
* As ABG is enabled, LPF values can likely be raised.
* Testing shown that ABG plus dynamic_filter is a bit much filtering, and likely ABG is best used without dynamic_filter, but this is not a hard rule and proper-tuning could be achieved irregardless.

### How does it work?
The ABG code creates a predictive filter that uses your velocity, acceleration and jerk to predict what the next gyro output will be. This creates a very low latency filter. 

* ABG_Alpha determines how much filtering is done. Higher values are less filtering and lower values relate to more filtering. 
* ABG_Boost is how quickly this filter reacts to very fast changes. More boost means that it will close large changes faster, thus reducing latency. 
* ABG_Half_Life determines how much of the past the filter relies upon. The default value of 50 means that after 0.5 seconds half of its history is gone. 

This filter is does not deal well with high noise and should normally not be used to replace a lowpass filter, but rather to work in tangent with a lowpass filter. This synergy is able to create a lower latency filtering setup overall even with the addition of more filters. My general recommendation is to set the ABG alpha to around 400+ and then raise your lpf filters to create a lower latency filter setup.

The settings on dTerm:
* `dterm_abg_alpha` (OSD: DTERM ABG ALPHA) Range 0-1000, default 0 (ABG dTerm off)
* `dterm_abg_boost` (OSD: DTERM ABG BOOST) Range 0-2000, default 275
* `dterm_abg_half_life` (OSD: DTERM ABG HL) Range 0-10000, default 50

The settings on Gyro:
* `gyro_abg_alpha` (OSD: GYRO ABG ALPHA) Range 0-1000, default 0 (ABG Gyro off)
* `gyro_abg_boost` (OSD: GYRO ABG BOOST) Range 0-2000, default 275
* `gyro_abg_half_life` (OSD: GYRO ABG HL) Range 0-10000, default 50

AB (αβ) filter reading is very helpful as well: https://en.wikipedia.org/wiki/Alpha_beta_filter

### ABG settings accessible via expert-mode
![ABG expert-mode](/assets/images/ABG-expert-mode.png)

***

**_@nerdCopter tip_**: `dynamic_filter` disabled and dTerm ABG alpha 600-800 is good enough for me.