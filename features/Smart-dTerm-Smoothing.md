---
layout: default
title: Smart dTerm Smoothing
parent: Features
nav_order: 11
---

# Smart dTerm Smoothing

`smart_dterm_smoothing_[roll|pitch|yaw]` is a dTerm minimizer based on how high dTerm is at any given moment.  It will reduce dTerm when it is small, but will allow full dTerm when it is big.  A value of 0 is off.  Default is 5 (0.5%) on Roll and Pitch, 0 on Yaw. Maximum allowed is 250 (25%). Smoothing mathematics does not cause delay.

You may enable debugging with `set debug_mode = SMART_SMOOTHING`.

When tuning from scratch, you may turn this off.

Racers may want to turn this off:
```
set smart_dterm_smoothing_roll = 0
set smart_dterm_smoothing_pitch = 0
set smart_dterm_smoothing_yaw = 0
```

Defaults:
```
set smart_dterm_smoothing_roll = 5
set smart_dterm_smoothing_pitch = 5
set smart_dterm_smoothing_yaw = 0
```