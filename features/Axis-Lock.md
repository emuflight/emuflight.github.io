---
layout: default
title: Axis lock
parent: Features
nav_order: 17
---

# Axis lock
{: .no_toc }

---

### 0.4.0+
* Axis-Lock significantly reduces pidsum for opposing axes giving importance to the current stick input and making the quad feel more locked-in.
 
The effect of Axis-Lock creates a quad that feels more locked. Axis that you do not mean to be controlling are ignored and only the axis you are controlling is stabilized. This effect only happens while moving your sticks, once in a steady state the effect does nothing.

* axis_lock_multiplier determines how strong the effect is. A value of 0 disables it.
* axis_lock_hz is the filter freq at which we filter your rc command to create the effect. Lower Hz take longer for the effect to appear, but the effect lasts longer than if the Hz is set high.

This is a personal feel type setting. Many pilots enjoy a lock multiplier of 5 with a hz of 2+. Play around with this yourself and see how it feels. Angle mode pilots particularly enjoy the extra feel that they can get out of their angle mode flying.
```
# get axis_lock

axis_lock_multiplier = 0
profile 0
Allowed range: 0 - 10

axis_lock_hz = 2
profile 0
Allowed range: 1 - 50
```

Axis-Lock feature is off when axis_lock_multiplier is zero.

***

Axis-Lock idea help from @Mainbrain