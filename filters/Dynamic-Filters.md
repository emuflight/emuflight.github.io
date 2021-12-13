---
layout: default
title: Matrix
parent: Filters
nav_order: 4
---

# Matrix
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Dynamic Filter on Gyro

* The gyro Dynamic_Filter in EmuFlight 0.3.X (a.k.a. Matrix) is a per-axis dynamic gyro notch written by [Paweł Spychalski](https://www.youtube.com/c/Pawe%C5%82Spychalski/search?query=matrix%20filter).
* 0.4.0+ upgrades the dynamic_filter in part with code from KarateBrot and calculations from QuickFlash

### Tuning
* EmuFlight stock defaults are fair for a 5" standard-frame quadcopter, but generally over-filter.
* Defaults have dynamic_filter enabled as well as 2 dTerm LPF's, which again may be overfiltering. (Helio is disabled by default.)
* **_The goal of filter tuning is to have a quad-specific tune that is neither over-filtered nor under-filtered._**

### Many options (0.3.X+)
* dynamic_filter may placed over the motor-noise spikes to remove dTerm noise from gyro; However,
* dynamic_filter may also be placed above motor-noise spike to clean-up only high frequency noise.
* Often it is found that with dynamic_filter enabled, only one dTerm LPF is required.
* Prior to 0.4.0, it was found that with dynamic_filter disabled, two dTerm LPF's were preferred if not required. (But this may vary with different aircraft, especially on Helio/Strix.)
* With 0.4.0+, dynamic dTerm notches may be enabled as the primary dTerm filter.  It seems a single dTerm LPF still helps in this situation, but allows for a much higher cutoff.

### Variables and Values
* Enable: `feature dynamic_filter`; Disable:`feature -dynamic_filter`
* Q (`dynamic_gyro_notch_q`) - Width of the dynamic per-axis notches. Higher value is a narrower notch, while smaller values are a wider notch. Smaller values (wider notches) are more latent than larger values (narrower notches). Range: 1-1000. Default: `350`.
* `dynamic_gyro_notch_count`   Range 1-5, Default 3. (0.4.0+)
* Min (`dynamic_gyro_notch_min_hz`) is the lowest value that a notch's cutoff may exist. Range: 30-1000. Default: `150`.
* Max (`dynamic_gyro_notch_max_hz`) [0.3.2+ / CLI only] is the highest value that a cutoff may exist. 0.4.0-Range is 400-1000. 0.3.0-Range is 600-1000. Default: `600`.

## Dynamic Filter on D-Term
  - uses the analysis of the gyro dynamic filter to apply d-Term notches
  - `dterm_dyn_notch_enable` Range ON, OFF. Default OFF.
  - `dterm_dyn_notch_q` Range 1-1000, Default 400.

### "Q" Example Graphic
![example dynamic_filter Q](/assets/images/example_dyn-filter_Q.png) **Q** (`dynamic_gyro_notch_q`) is a width. (_note\*: graphical representation only, not necessarily actual size._)

### Dynamic Filter was formerly "Matrix"
![Paweł Spychalski matrix Screenshot](/assets/images/Screenshot_Matrix.jpg)
* Matrix Introduction, by Paweł: https://youtu.be/7s8ZeP135uI
* How it Works, by Paweł: https://youtu.be/w0QsVIXYWCE

