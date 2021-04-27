---
layout: default
title: What is EmuFlight?
parent: Getting Started
nav_order: 1
---

# What is EmuFlight?

**Purpose of EmuFlight**

EmuFlight is a fork of Betaflight with a focus on flight performance and ease of use. EmuFlight aims to better the drone racing and freestyle community in all aspects, including user support, documentation, software testing, and creating a healthy work environment for developers and pilots. EmuFlight differs from Betaflight in flight code, methodology and purpose. Hardware support and general setup between EmuFlight and Betaflight continues to be near identical. EmuFlight stays up to date with the latest Betaflight merging almost all code changes, the main differences being related to flight code. For ease of use EmuFlight uses the Nemesis configurator which is another deviation from Betaflight. Due to the small development team of EmuFlight we don't have the development resources that Betaflight does, and as a result we share most our code and will improve as Betaflight improves. At some point in the future EmuFlight may deviate from Betaflight to a larger extent.

**Origins**

HelioRC, was a company that made unique flight controllers for racing/freestyle drones. Eventually HelioRC went out of business and stopped supporting any of their products, however, as a final gift they made all of their code opensource. EmuFlight was inspired by the work which HelioRC had done and created a fork of the now defunct software Butterflight, which was another fork of Betaflight, in the summer of 2019. One of the first things that EmuFlight added to the code was to port over some of the code that HelioRC had made and to begin updating the code HelioRC had made for their products. Since then EmuFlight has seen many changes from the first release version 0.1.0, in September of 2019, to the last Butterflight based version 0.4.0, in the summer of 2021.

Moving forward EmuFlight has decided to rebase the code and take what was learned in making EmuFlight and apply it to the latest version of Betaflight. This catches EmuFlight up with many hardware changes,  flight improvements, and quality of life updates that have occurred over the past 3 years as Butterflight was last up to date with Betaflight in the summer of 2018. Moving forward EmuFlight will stay up to date with the latest Betaflight code changes, while still maintaining what makes EmuFlight unique. This will ensure that development efforts on EmuFlight can be focused provide meaningful improvements while still providing users with much wanted features from Betaflight.


# What makes EmuFlight different than Betaflight?

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
