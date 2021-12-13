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

### Please note that 0.4.0+ adds PT2, PT3 and PT4. Some of these recommendations may not apply in the same manner.

### Should I use 1 or 2 dTerm LPF's?
* Depends on your quad's physical characteristics or if you use [Dynamic_Filter](https://github.com/emuflight/EmuFlight/wiki/Dynamic-Filters).
* The default Dynamic_Filter ON and two dTerm filters is generally over-filtered.
* Dynamic_Filter ON and one _tuned_ dTerm LPF is good.
* Dynamic_Filter OFF and two _tuned_ dTerm filters is good.

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

_**@JulioCesarMatias tip**_: PT1 filter, for example, reduces the signal power by half at the cutoff. A second-order filter attenuates high frequencies more steeply than a first. Third- and higher-order filters are defined similarly.


### Per-Axis Tuning
* Historically in most flightware, a single lowpass filter cutoff value applied to all axes (Roll, Pitch, Yaw).  However EmuFlight allows for per-axis tuning as each noise axis usually have differing noise profiles.  Per-Axis settings are accessible via expert-mode.
![Per-Axis filtering](/assets/images/per-axis-filtering.png)



### Notable Filtering resources:
 - https://oscarliang.com/betaflight-filtering/
 - https://github.com/betaflight/betaflight/wiki/Gyro-&-Dterm-filtering-recommendations
 - https://www.propwashed.com/notch-filter-practical-guide/

***
Although not precise, this image represents the basic idea of LPF tuning:

![Basic LPF Theory](/assets/images/basic_theory.png)

***

This example, you can see clearly how the PT1 filter cleaned the noise. Although in this situation, 65Hz is too low for good performance.

![PT1 applied too low](/assets/images/too-low-but-see-it.png)

***

This example shows motor dTerm motor noise at a very low Hz. A fair dTerm LPF cutoff could be 85hz. Possibly, any value 70-90 may work.  90 may offer best control and prop-wash handling at the cost of a little heat. If propellers get bent, then motors could potentially get too warm.  Lower of 70 may offer heat protection, but at the cost of poor prop-wash handling.  Tuning is always a cost/benefit analysis.  Here this low Hz is not typical, but only used as an example:

![Low Hz Motor Noise Example](/assets/images/lowHz_motor_example.png)

***

### Further examples:

Roll Gyro noise -- place LPF in vicinity of red arrow:

![](/assets/images/example1-Roll-gyro-gLPF1-generalPlacementArrow.png)

Roll D-Term noise -- place LPF1 in vicinity of red arrow:

![](/assets/images/example1-Roll-dTermR-dLPF1-generalPlacementArrow.png)

Pitch D-Term noise -- place LPF2 in vicinity of red arrow:

![](/assets/images/example1-Pitch-dTerm-dLPF2-generalPlacementArrow.png)

PID oscillation from too low or too delayed filters:

![](/assets/images/example-oscilation-from-too-low-or-delayed-filters.png)

_**@QuickFlash Tip:**_ If your pids oscillate in harmonics, then likely your pid balance is wrong or your filters are set too low and adding too much delay. You can see how it starts small and grows over time. That's feedback from the system. That's why those oscillations don't go away. It feeds itself.

