---
layout: default
title: LowPassFilters
parent: Filters
nav_order: 1
---

# LowPassFilters
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### Low-Pass Filter (LPF) tuning is a must!
* Over-filtering can cause problems.
* Under-filtering can cause problems.
* EmuFlight stock defaults are fair for a 5" standard-frame quadcopter, but generally over-filter.
* The goal of filter tuning is to have a quad-specific tune that is neither over-filtered nor under-filtered.

### Should I use a PT1 or BIQUAD?
* Some quadcopters seem to be happier with a PT1 while other quadcopters seem to prefer a BiQuad.
* Gyro and dTerm LPF type can be set independently. 
* Generally the PT1 seems to produce less problems than the BiQuad, but in certain circumstances the BiQuad is better.
* PT1 filters less and therefore has less latency.
* PT1 may be more responsive.
* dTerm PT1 may be less tolerant of high dTerm values and propeller damage.
* BiQuad filters more thoroughly and therefore may have more latency.
* BiQuad over-filtering could be a problem though and having to much of a good thing isn't necessarily good for flying.
* dTerm BiQuad may be more tolerant of high dTerm values and propeller damage.

### Should I use 1 or 2 dTerm LPF's?
* Depends on your quad's physical characteristics or if you use [Matrix](/filters/Matrix.html) Filter.

### Notable Filtering resources:
 - https://oscarliang.com/betaflight-filtering/
 - https://github.com/betaflight/betaflight/wiki/Gyro-&-Dterm-filtering-recommendations
 - https://www.propwashed.com/notch-filter-practical-guide/

***
Although not precise, this image represents the basic idea of LPF tuning:

![Basic LPF Theory](/assets/images/basic_theory.png)

***

This example shows motor dTerm motor noise at a very low Hz. A fair dTerm LPF cutoff could be 85hz. Possibly, any value 70-90 may work.  90 may offer best control and prop-wash handling at the cost of a little heat. If propellers get bent, then motors could potentially get too warm.  Lower of 70 may offer heat protection, but at the cost of poor prop-wash handling.  Tuning is always a cost/benefit analysis.  Here this low Hz is not typical, but only used as an example:

![Low Hz Motor Noise Example](/assets/images/lowHz_motor_example.png)