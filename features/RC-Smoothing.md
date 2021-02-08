---
layout: default
title: RC Smoothing
parent: Features
nav_order: 10
---

# RC Smoothing

RC Smoothing is a personal preference and may be specific to components used.  RC Smoothing is CPU intensive. Generally, BiQuad is smoother at cost of minor delay and PT1 faster at cost of minor less smoothness.

***@3dracingman Tip:*** Racers should leave RC Smoothing defaults.  For freestylers, if not using BBL to analyze RC Command, then Interpolation is a good start.  I have spent many hours of testing and concluded the following personal preference:
```
set rc_interp_ch = RPYT
set rc_smoothing_type = FILTER
set rc_smoothing_input_hz = 50
set rc_smoothing_derivative_hz = 75
set rc_smoothing_input_type = BIQUAD
set rc_smoothing_derivative_type = BIQUAD
```

***@Skylion Tip:*** I use the following on every quad for Crossfire, but the 55hz input is subjective -- up to 65 for a larger quad, or down to 45 for a micro.
```
set rc_interp_ch = RPYT
set rc_smoothing_type = FILTER
set rc_smoothing_input_hz = 55
set rc_smoothing_derivative_hz = 100
set rc_smoothing_input_type = PT1
set rc_smoothing_derivative_type = PT1
```

***@Ian444 Tip:*** [Interpolation] 19mS works too, I stayed at 21mS for a bit of margin.
Under 19mS gets rough. That's with [FrSky SBUS] D8. I think D16 same, not sure.



***

Many online resources also recommend disabling the ADC Filter in OpenTX ![Disable ADC Filter](/assets/images/disable-ADC.png)
