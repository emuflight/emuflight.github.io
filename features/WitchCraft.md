---
layout: default
title: Witchcraft
parent: Features
nav_order: 14
---

# Witchcraft

`witchcraft_[roll|pitch|yaw]` smooths dTerm over time. The value is how many pid loop iteration samples are averaged to calculate dTerm. A value of 0 or 1 is effectively off. Default is 2 on Roll and Pitch, 0 on Yaw. Maximum allowed is 10. May cause delay.

WitchCraft has more effect as feathered PIDs are lower and less effect as feathered PIDs are higher.

When tuning from scratch, you may turn this off.

Racers may want to turn this off.

```
set witchcraft_roll = 0
set witchcraft_pitch = 0
set witchcraft_yaw = 0
```

Defaults:
```
set witchcraft_roll = 2
set witchcraft_pitch = 2
set witchcraft_yaw = 0
```
