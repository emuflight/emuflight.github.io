---
layout: default
title: Sharpness
parent: Filters
nav_order: 3
---

### Sharpness has been _**removed**_ in 0.4.0+

In essence, increasing `sharpness` makes the filter more dynamic which will lead to less filtering. It reduces over-filtering.

More technically, `sharpness` effects how much of a dynamic multiplier gets added to the base filtering value. For example, considering IMUF/Gyro LPF's, at say 50hz it doesn't have to do as much to increase your filtering frequency as it does at 10hz. At 10hz it needs to boost that base filter a ton more to give you more snappy feels and better propwash handling. But that lower base helps by in a sense overfiltering when it isn't a problem and then filtering less when overfiltering would be a problem.

Generally it's a good idea to turn Sharpness off while trying to tune. Such will allow you to tune Q without additional dynamic behavior..  That said, depending on which non-Helio release/build or Helio IMUF Binary, there may differing way of turning sharpness off or "near" off
* 0.3.2+ non-Helio: `set sharpness = 0`
* 0.3.2+ Helio IMUF 250: `set sharpness = 0`
* 0.3.2+ Helio IMUF 230, 231: `set sharpness = 250` or `set sharpness = 1` \*debatable which is best -- see additional info near bottom.
* 0.3.1 non-Helio:  `set sharpness = 250` or `set sharpness = 1` \*debatable -- see additional info near bottom.

Once a good Q range is estimated, then one could introduce sharpness.  As more sharpness is introduced, Q should be reduced.

Generally, but not always, a few good options are:
 1) Sharpness off; only tune Q.
 2) very-low Q; medium-high Sharpness.
 3) high Q; very-low Sharpness.

Generally, you do not want high Q with high Sharpness -- i.e. Although good to not over-filter, you also don't want to ultra-Under-Filter.

***

**Additional Information**
* For 0.3.1 and Helio IMUF 230,231 sharpness was simply something like thus:
```c
    filter->s = gyroConfig()->imuf_sharpness / 250.0f;  
[...]
    float errorMultiplier = fabsf(target - kalmanState->x) * kalmanState->s;
```
* However in 0.3.2+ and IMUF 250, sharpness is more complex, something like:

```c
[...]
  if (kalmanState->s != 0.0f) {               //if sharpness non-zero
    float average = fabsf(target + kalmanState->lastX) * 0.5f;
    if (average > 10.0f) {
        float error = fabsf(target - kalmanState->lastX);
        float ratio = error / average;
        kalmanState->e = kalmanState->s * powf(ratio, 3.0f);  //"ratio" power 3 and multiply by a gain (sharpness)
    }
    //prediction update
    kalmanState->p = kalmanState->p + (kalmanState->q + kalmanState->e);
  } else {          //if sharpness zero (off)
    if (kalmanState->lastX != 0.0f) {
        kalmanState->e = fabsf(1.0f - (target / kalmanState->lastX));
    }
    //prediction update
    kalmanState->p = kalmanState->p + (kalmanState->q * kalmanState->e);
  }
[...]
```
 

