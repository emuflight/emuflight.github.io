---
layout: default
title: Rate Dynamics
parent: Features
nav_order: 8
---

# Rate Dynamics
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Rate Dynamics 
Rate Dynamics is a stick-feel modifier.  This may be one of EmuFlight's greatest achievements for 0.3.0 as it allows the pilot to achieve any input control characteristics desired. Rate Dynamics is essentially a PID controller for RC Command.  In simplest terminology, it either delays or overshoots RC command.  Normal RC Rates still apply.

## How do Rate Dynamics work?
 Rate Dynamics allows your rates to change dynamically based on how you move your sticks. This results is the ability to choose aggressive racing feel, smoother freestyle feel, or a super super cinematic feel on the sticks. 

Center and End determine how the rate dynamics effect the stick feel during the center or end of the stick. Center will effect your stick feel near the center of the stick and end effects the feel at the end of the stick. The three parameters that effect rate dynamics are Sensitivity, Correction and Weight. Sensitivity adds a boost or shrink to your rates and makes your quad feel more "sensitive", hence the name. This boost is seen as a percentage. The default of 100 does nothing while a value of 120 boosts your rates by 1.2 and a value of 80 shrinks your rates by a value of .8! Correction is a value that will over time correct for the boost or shrink in rates caused by your sensitivity. The higher the correction the quicker it corrects for the boost or shrink in rates. Weight apposes all change to the setpoint which makes the sticks feel as though you have added some weight to them, hence the name. This number is seen as a percentage. A value of 0 does nothing while a value of 50 apposes 50% of the change in your rates. This smooths out your sticks and if used to a very large values will add delay, but can make your sticks look very cinematic. While weight does add some "latency" to the sticks everyone that has tested this feature uses at least some weight as it does quite a good job of smoothing things out. Even race pilots will use weight, just counteracted with extra sensitivity to counteract the "latency" that it adds leading to a sharp, yet smooth, fast reacting quad that handles well for racing.

## Different Rates

The following are preliminary estimates for desired feel.  This may change as more pilots provide feedback.  You may use these as a base, then tune to your preference.


**Defaults** - no rate change
```
set rate_center_sensitivity = 100
set rate_center_correction = 10
set rate_center_weight = 0
set rate_end_sensitivity = 100
set rate_end_correction = 10
set rate_end_weight = 0
```

**Cinematic** - Very smooth center-stick.  These settings drastically slow down instant moves near the center of the stick, but leaves end-of-stick untouched.  This will feel less responsive but should result in very smooth video footage. The high weight near the center does a very good job of smoothing out all stick movements near the center of your stick.
```
set rate_center_sensitivity = 80  #or less
set rate_center_correction = 20   #or less
set rate_center_weight = 85       #or more
set rate_end_sensitivity = 90     #or less
set rate_end_correction = 10      #or more
set rate_end_weight = 50          #or more
```

***Kebab FPV CineWhoop Super Cinematic*** - Very anemic near the stick center and very numbed down feeling. Perfect for never over correcting and causing unwanted sharp movements. For best stick feel this probably isn't for you, but if you want to fly super smooth with little effort try this

```
set rate_center_sensitivity = 55  
set rate_center_correction = 25   
set rate_center_weight = 90       
set rate_end_sensitivity = 100    
set rate_end_correction = 10      
set rate_end_weight = 50          
```

**Freestyle** - This is a very open-to-modification estimate because this style is a strong personal preference to individual pilots. These settings should smooth the center-stick some, yet still allow quick flips to be very fast.  It should also smooth the entire movement overall.
```
set rate_center_sensitivity = 80
set rate_center_correction = 10
set rate_center_weight = 35
set rate_end_sensitivity = 130
set rate_end_correction = 10
set rate_end_weight = 35          #or less
```

**Racing** - These settings should smooth center-stick a little while still providing an aggressive and responsive feel overall.
```
# racing
set rate_center_sensitivity = 130
set rate_center_correction = 35
set rate_center_weight = 30
set rate_end_sensitivity = 115
set rate_end_correction = 20
set rate_end_weight = 10
```


***
@fichek Tip: one thing I instantly noticed is the bounceback when there is over 100% sensitivity on stick end and low weight and/or correction - so the recommended freestyle preset is a bit too springy imo...

[@fichek's Rate Simulator](https://stoot.tech/emu-rate-dynamics.html){: .btn .btn-blue }