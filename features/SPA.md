---
layout: default
title: SPA
parent: Features
nav_order: 12
---

# SPA
In EmuFlight 0.2.0 and above, we now have SPA Rates (Stick Position Attenuation).

The values will multiply against the P, I, or D (whichever you set). At full-stick deflection the values will be maximum but will be less at mid-stick deflection.

examples:
- 100 equals 100% (i.e. no change)
- 65 equals 65% at full-stick deflection
- 125 equals 125% at full-stick deflection

The big quads are using it to add a bunch of D at full-stick deflection to mimic Min_D/Max_D. (ex. Low Roll/Pitch D & SPA_D = 120)

Or for whoops, SPA can be used to have extremely high I_term on yaw which can be significantly softened in turns. (ex. Yaw I_Term 120 and Yaw SPA_I 20)
