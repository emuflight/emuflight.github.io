---
layout: default
title: Direct Feed Forward
parent: Features
nav_order: 16
---

# Direct Feed Forward
{: .no_toc }

---

Direct Yaw Feed Forward - https://github.com/emuflight/EmuFlight/pull/438
* Yaw acts different than pitch and roll. This adds a feedforward based on setpoint. The more setpoint the higher the yaw ff, so just moving your setpoint will make an addition to the pidsum. The idea is that yaw always needs some motor output in order to create a yaw movement whereas pitch and roll just needs a push to start the move. The idea is to tune the true yaw FF so that it is pretty close to what the yaw needs to spin at that rate. This reduces the amount of iterm windup that happens with iterm. This allows yaw to act faster and have less iterm windup.
* Also allowing for direct ff low and high for angle modes. Direct ff does work fine in angle mode as angle mode could fly with exclusively just direct ff and all pid gains set to 0, as such direct ff only works for pitch and roll while in angle mode and this only allows for that.
* CLI
  - `df_yaw` Range 0-200. Default 15.
  - `df_angle_low` Range 0-200. Default 70.
  - `df_angle_high` Range 0-200. Default 0.
