---
layout: default
title: IMUF
parent: Filters
nav_order: 2
---

# IMUF
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### IMUF Tuning

## Q
Think of Q as “Trust”. The more you “trust” the gyro measurement, the less filtering will be applied. Q values are “elastic”. The defaults (3000) are now baseline values. This will predictably change based on conditions during flight. This results in a much more responsive and connected feel. This also reduces the potential for MTO, and other unwanted flight characteristics. In some instances MTO can be created from having a Q value which is to low. In those instances increases Q will help with MTO.

***@Skylion tip:*** I generally start with Q around 5000-6000 and start raising Q by 500 at a time till it starts to "feel bad" or till you notice something weird (yaw twitches, bobbles, over shooting, etc). The idea is the higher you can raise q the less filtering there will be on your gyro which makes the quad feel more "locked in". If your quad starts feel like it's less in your control after you've just raised q then lower it back down by 500. Another method is to just raise it till it feels like there is no delay between your stick movements and how the quad reacts then leave it there. I've seen most people use anywhere from 5000-9000 successfully, 16000 is the maximum.

***@Pierre Meunier tip:***  Larger quads tend to use Q's on the low-end of the value range, while smaller quads tend to use higher values.  E.g. 7": 4000±  5": 6000±

***@nerdCopter tip:***  Clean gyros and clean builds tend to use higher Q's, but noisy builds or bad gyros tend to need lower Q values.  Helio/Strix can use higher Q's out of the box just due to it's excellent filtering capability. E.g 6000±/7000±.

## Sharpness (0.3.X+)
EmuFlight has also introduced Sharpness to reduce over-filtering.  Please see the [Sharpness](/filters/Sharpness.html) article as it has direct affect on Q.

## W
W is the amount of gyro readings which the IMUF filter looks at to determine its filter. Lower W gives a sharper stick feel. Larger craft prefer a higher W value. Increasing W does not increase delay in the filter, instead it just increases the window of gyro readings from the past that the filter looks at to make its calculations. The default for a typical 5" quadcopter is 32. Generally, racers may prefer a lower W while freestylers may prefer a larger W. While a lower W may reduce smoothness, it may also assist in cutting through heavy winds -- consider using profiles for low-wind vs high-wind days.

***@nerdCopter tip:***  Learning from others, it's now common knowledge that smaller quads prefer lower W and larger quads prefer larger W.  `imuf_w=32` is good default for 5", while for 6" i personally use `64` and 7" i use `128`.  @3Dracingman suggested `10` for whoops. We tend to use values divisible by 8, but there is no hard-rule. You could use any value and range as desired. Increasing W also assists with smoothing out nose dips on throttle blip.

***@Skylion Tip:*** W seems to have more of a correlation to the size of your craft and the style of your flying than anything. So for example if your tuning a tiny whoop/toothpick/micro2"-3" your W will feel good anywhere between 16-48, 4"-6" can be happy anywhere between 16-64, 7"+ tend to be happy from 64-256, X-Class will like 300+, the bigger the props the higher the W. Also if you're racing you will probably prefer a lower W than if your freestyling. Also I've found that W likes to be set to a multiple of 8 but I highly suggest going back and forth and choosing the W setting that flies best for you.



## Tuning Flowchart
Use the following Flowchart for basic PID tuning.  Start by disabling Dynamic-Filter, TPA, Anti-Gravity, SPA, EmuBoost, Sharpness & for older versions, FeedForward while achieving a good tune.  Then re-enable or modify features as needed for further fine-tuning.

![Tuning](/assets/images/EmuFlight-Tuning.jpg)