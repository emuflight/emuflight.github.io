---
layout: default
title: TPA
parent: Features
nav_order: 13
---

# TPA

In EmuFlight the TPA works completely differently than in BetaFlight. TPA in EmuFlight has been split into P, I and D. TPA as well has changed so that instead of TPA being the amount that your PIDs are cut it is instead the percentage your PIDs will be at full throttle. A TPA of 0.8 for example means that at Full throttle your PID is decreased to 80% of its normal value, whereas a value of 1.25 means that your PID is increased to 125% of its normal value. Your TPA values can vary from 0 up to 2.50. TPA has changed to be this way so that you can make TPA boost your PIDs (used mainly for I and sometimes P).

#### 0.3.X Defaults for TPA are:
* TPA P: `0.75` (75%)
* TPA I: `1.25` (125%)
* TPA D: `0.65` (65%)
* TPA Breakpoint `1600`

#### 0.2.0 Defaults for TPA are:
* TPA P: `0.65` (65%)
* TPA I: `1.25` (125%)
* TPA D: `0.50` (50%)
* TPA Breakpoint `1350`

#### Example graphs of TPA application at throttle
![Emu TPA first example](/assets/images/EMUF-TPA.png)
![Emu TPA second example](/assets/images/Emu_TPA_2.png)
