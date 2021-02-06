---
layout: default
title: iTerm Relax
parent: Features
nav_order: 7
---

# iTerm Relax

EmuFlight 0.3.2+ implements a simplified iTerm relax which is based only on setpoint and the `_INC` mode.

`iterm_relax_cutoff` is the setting for both Roll and Pitch (RP). `set iterm_relax_cutoff_yaw` is the setting for Yaw (Y).

Additionally, in 0.3.2+, `iterm_windup` value is now reversed.  So the default value of `70`, means windup accumulation will stop at 70% motor saturation.  In 0.3.1, default was `50` which would still be 50%.

Threshold is available in CLI, but does not typically need modification.

defaults:
```
set iterm_relax_cutoff = 11
set iterm_relax_cutoff_yaw = 25
set iterm_relax_threshold = 35
set iterm_relax_threshold_yaw = 35
set iterm_windup = 70
```

iTerm relax off:
```
set iterm_relax_cutoff = 0
set iterm_relax_cutoff_yaw = 0
```

for example, RP may be accomplished with:
```
set iterm_relax_cutoff = 11
set iterm_relax_cutoff_yaw = 0
```


For more information visit https://github.com/betaflight/betaflight/wiki/I-Term-Relax-Explained