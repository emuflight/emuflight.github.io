---
layout: default
title: Smith Predictor
parent: Features
nav_order: 16
---

# Smith Predictor
{: .no_toc }

---

## Smith predictor on Gyro

### 0.4.0+
* https://en.wikipedia.org/wiki/Smith_predictor
* https://www.controleng.com/articles/overcoming-process-deadtime-with-a-smith-predictor/

### How it works
The Smith predictor creates a model of the delay that your filters create. It creates this model by looking at past gyro data and using that to predict future gyro data. This essentially is almost a "free" way of reducing filter latency. This feature creates far better flight performance by reducing the effective delay of gyro filtering. A downside however is that very noisy gyro data will act worse with this feature on, but the upside is that this feature helps to reduce latency and thus a slightly more filtered quad will still fly extremely well.

* Smith_Predict_Enabled turns on or off the Smith predictor
* Smith_Predict_Str determines how much of the prediction to be used. A value of 50 means that we only use 50% of our prediction. Since the prediction tends to slightly overshoot limiting the str is advised.
* Smith_Predict_Delay is us telling the smith predictor how many ms/10 of delay we assume that the filtering provides. Higher values are for more highly filtered gyro signals and lower values for less filtered quads. The default works surprisingly well.
* Smith_Predict_Filt_Hz is the frequency in which we filter our Smith predictor. Predictions of future events is inherently noisy and the Smith predictor is no exception. By filtering the Smith predictor we can remove any harmful effects of that added noise. For very clean quads this can be raised and even more performance from the Smith predictor can be had.

```
smith_predict_enabled = ON
Allowed values: OFF, ON

smith_predict_str = 50
Allowed range: 0 - 100

smith_predict_delay = 40
Allowed range: 0 - 120

smith_predict_filt_hz = 5
Allowed range: 1 - 10000
```

The enabled toggle is the only item in the EmuConfigurator.  Defaults are good for most aircraft.

***@Paweł Spychalski Tip***:  Smith predictor amplifies a bad/noisy gyro.  Disable Smith-predictor on such quads. (Paraphrased)