---
layout: default
title: What makes EmuFlight different?
parent: Getting Started
nav_order: 2
---

# What makes EmuFlight different?

EmuFlight is a fork of ButterFlight that has had many additions making it worthy of attention. Most notably is the addition of the Helio IMUF filtering on all flight controllers. With EmuFlight being a fork of ButterFlight, EmuFlight is quite similar to betaflight 3.5 except with many improvements making the switch to EmuFlight very worthwhile.

**What features does EmuFlight have that Betaflight does not?**
* Feathered PIDs (previously Buttered PIDs, calculating the dterm using measurement which is smoother)
* IMUF filtering on all flight controllers
* i_decay (unique way of handling iTerm building during quick moves)
* EmuBoost and BoostLimit (creates an enhanced nonlinear pid controller (better noise handling when tuned) changes stick feel more organically than feedforward)
* EmuFlight uses different methods to calculate dTerm filtering than Betaflight (tuning dTerm and dTerm filters remains easier than before)
* GPS has been updated to allow for a sort of geofencing to make flying in French regions legal
* TPA is split into kP, kI and kD
* TPA can be a boosting factor now. Especially useful in conjunction with the iTerm
* AKK VTX hack on each build (no longer the need to download a special branch for this!)

**New in the 0.2.0-RC1 Milestone**
* Dropped F3 support
* Community provided preset-tunes in the Configurator
* Fixes to the IMUF filter for non-Helio FC
* Updates to the IMUF filter for Helio FC New IMUF version 211, 213
* NFE RacerMode (NotFastEnuf racermode is Angle-mode on roll axis only)
* Cinematic Yaw (Whoop feature mixes roll and yaw based on pitch angle)
* Changes to Feathered PIDS (Feathered PIDs now variable 0% to 100% and works with FeedForward)
* Motor Output Limit
* Stick Position Attenuation AKA SPA Rate (Similar to TPA but based on stick deflection instead of throttle)
* Helio FC now have full use of the dynamic notch filter
* Support for JESC Configurator
* Ability to set the LPF filter for voltage and current (can now have quicker updating voltage readings)
* Fixed yaw PIDsum limit
* Improved telemetry causing PIDloop jitters
* Dynamic Gyro LPF and Dynamic dTerm LPF (still experimental)
* EmuBoost split into Pitch/Roll and Yaw (tune EmuBoost separately for yaw)

**New in 0.3.X** (and some 0.2.XX dev versions)
* [Smart_dTerm_Smoothing](/features/Smart-dTerm-Smoothing.html) (Decreases d near small d values. The higher you run smart_dterm_smoothing the more it will attenuate low dTerm values and it will also start attenuating larger dterm values. It smooths dterm by comparing the average of the last two dTerm readings and shrinks dTerm more near small values. `50`=5% as seen in blackbox logs. Because of how this works it can essentially be used as a form of Dmin, removing the annoyance of dterm noise when the quad is hovering while still giving you access to the full dTerm effect to help during quick movements or propwash.)
* [WitchCraft](/features/WitchCraft.html) (Smooths dTerm over time; it may help remove bobble when D acts before P. It averages the last _`x`_ samples of DTerm.)
* Full PID controller for [Angle and NFE-Racer modes](/features/Angle-and-NFE-Racer-modes.html) very similar to the angle controller in silverware (Previously P-only) (Now, technically P&D, no I)
* Removal of unnecessary Dynamic LPF's
* SPA per axis
* Gyro and dTerm LPF's per axis
* `sharpness` for both Helio IMUF and and non-Helio flight controllers
* rateDynamics
* vbat compensation
* turtle-mode motor power adjustment
* iDecay v2 (0.3.2+)
* DBoost (0.3.2+)
* Simplified iTerm Relax (0.3.2+)
* CRSF LQ display

**0.3.3+**
* [Mix Roll and Yaw](/features/Angle-and-NFE-Racer-modes.html#mix-roll-and-yaw) (a.k.a Dual Axis Steering) 
* NFE on an aux-mode switch.
* `set show_altered_rc = ON` in order to see what your RC looks like (in Configurator).
* Make rateDynamics feel the same irregardless of RX rate
* Immersion RC Ghost protocol
* [VTX power on an aux-mode switch](/Faq%20and%20Issues.html#vtx-power-on-an-aux-mode-switch) (CLI only)
* Ability to turn off Kalman prediction, but why would you want to? `set imuf_w = ` <= `2` to see why Kalman is better.
* LQ widget style selection in OSD.
* Added CRSF style `SCALE` for 170-300, and `SIMPLE` for 0-100 (a.k.a `100 for Days`)
* Backports of many enhancements, please check release notes.

**0.4.0+** (not yet released)
* Optional features: New Motor Mixer, Thrust Linearization and Throttle Linearization.
