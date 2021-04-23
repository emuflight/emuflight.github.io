---
layout: default
title: Full Parameter List
parent: Parameter List
nav_order: 1
---

# Full Parameter List

## List of all the cli parameters in EmuFlight 1.0.0 (still a work in progress)

| Parameter Name | Description | Min/Max/Table | Default | Units |
|----------------|-------------|---------------|---------|-------|
| gyro_hardware_lpf | Filter that the gyro hardware produces. Normal is suggested. | NORMAL, EXPERIMENTAL | NORMAL | |
| gyro_high_range | Increases the max DPS that your gyro can read. Only works for some gyros. (list those later) | ON, OFF | OFF |  |
| gyro_lowpass_type | Filter order for the gyro lowpass filter. Higher orders have sharper cutoff. | PT1, PT2, PT3, PT4 | PT1 | |
| gyro_notch1_hz | Center frequency for a notch filter placed on the gyro. A value of 0 disables the filter. | 0-4000 | 0 | Hz |
| gyro_notch1_cutoff | Cutoff frequency for the gyro notch filter. | 0-4000 | 0 | Hz |
| gyro_abg_alpha | Alpha value for a Alpha Beta Gamma filter on the gyro. Alpha Beta Gamma filters are simplified forms of observer for estimation, data smoothing and control applications. Higher values are less filtering and lower values filter more. When set to low the data lags, but to high and it doesn't do a whole lot of filtering. | 0-1000 | 0 |  |
| gyro_abg_boost | A non-linear boost to the error which the Alpha Beta Gamma filter uses in its calculations. Higher boost will make the Alpha Beta Gamma filter more responsive, but a bit noisier. | 0-2000 | 375 |  |
| gyro_abg_half_life | Reduces the scope of data which the Alpha Beta Gamma filter uses to make its prediction. The default of 50 means that after half a second the Alpha Beta Gamma remembers only half of the history. This makes the Alpha Beta Gamma filter rely more on newer data rather than old data. | 0-1000 | 50 | Seconds/100 |
| gyro_calib_duration | The amount of time used for gyro calibration. | 50-3000 | 125 | Seconds/100 |
| gyro_calib_noise_limit | Noise level the gyro must be below during the gyro calibration | 0-200 | 48 |  |
| gyro_offset_yaw | Meant to deal with yaw attitude drift. Only works when board are aligned normally and not exotically. The basic setup can be done on the bench without LiPo, USB powered power on, do not move the quad for 10 minutes for CW set a positive value equal to the drift, and negative for the CCW direction. | -1000-1000 | 0 |  |
| imuf_roll_q | Trust value for the kalman filter on the roll axis. (need to finish this) | 0-16000 | 3200 |  |
| imuf_pitch_q | Trust value for the kalman filter on the pitch axis. (need to finish this) | 0-16000 | 3200 |  |
| imuf_yaw_q | Trust value for the kalman filter on the yaw axis. (need to finish this) | 0-16000 | 3200 |  |
| imuf_w | Number of samples the kalman filter looks at for its prediction. Larger drones generally fly better with higher w values. | 0-300 | 32 |  |
| gyro_overflow_detect |  | OFF, YAW, ALL | ALL |  |
| yaw_spin_recovery |  | OFF, ON, AUTO | AUTO |  |
| yaw_spin_threshold |  | 500-1950 | 1950 | deg/sec |
| gyro_use_32khz |  | OFF, 16K, 32K | OFF |  |
| gyro_to_use |  | FIRST, SECOND, BOTH | FIRST |  |
| leaving space for dyn notch stuff |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
| dyn_lpf_gyro_min_hz |  | 0-1000 | 115 | hz |
| dyn_lpf_gyro_width |  | 0-255 | 0 | % |
| dyn_lpf_gyro_curve_expo |  | 0-10 | 5 |  |
| dyn_lpf_gain |  | 0-200 | 0 |  |
| gyro_filter_debug_axis |  | ROLL, PITCH, YAW | ROLL |  |
| smith_predict_str |  | 0-100 | 50 |  |
| smith_predict_delay |  | 0-80 | 40 | ms/10 |
| smith_predict_filt_hz |  | 0-10000 | 5 | Hz |
| acc_hardware |  |  |  |  |
| acc_high_range |  |  |  |  |
| acc_lpf_hz |  | 0-400 |  | Hz |
| acc_trim_pitch |  | -300-300 | 0 |  |
| acc_trim_roll |  | -300-300 | 0 |  |
| acc_calibration |  |  |  |  |
| align_mag |  |  |  |  |
| mag_align_roll |  | -3600-3600 | 0 | deg/10 |
| mag_align_pitch |  | -3600-3600 | 0 | deg/10 |
| mag_align_yaw |  | -3600-3600 | 0 | deg/10 |
| mag_bustype |  |  |  |  |
| mag_i2c_device |  |  |  |  |
| mag_i2c_address |  |  |  |  |
| mag_spi_device |  |  |  |  |
| mag_hardware |  |  |  |  |
| mag_calibration |  |  |  |  |
| baro_bustype |  |  |  |  |
| baro_spi_device |  |  |  |  |
| baro_i2c_device |  |  |  |  |
| baro_i2c_address |  |  |  |  |
| baro_hardware |  |  |  |  |
| baro_tab_size |  |  |  |  |
| baro_noise_lpf |  | 0-1000 |  | Hz |
| baro_cf_vel |  | 0-1000 |  |  |
| mid_rc |  | 1200-1700 |  |  |
| min_check |  |  |  |  |
| max_check |  |  |  |  |
| rssi_channel |  |  |  |  |
| rssi_src_frame_errors |  |  |  |  |
| rssi_scale |  |  |  |  |
| rssi_offset |  | -100-100 |  |  |
| rssi_invert |  |  |  |  |
| rssi_src_frame_lpf_period |  |  |  |  |
| rc_interp |  |  |  |  |
| rc_interp_ch |  |  |  |  |
| rc_interp_int |  |  |  |  |
| rc_smoothing_type |  |  |  |  |
| rc_smoothing_input_hz |  |  |  |  |
| rc_smoothing_derivative_hz |  |  |  |  |
| rc_smoothing_debug_axis |  |  |  |  |
| rc_smoothing_input_type |  |  |  |  |
| rc_smoothing_derivative_type |  |  |  |  |
| rc_smoothing_auto_smoothness |  |  |  |  |
| rc_predictor_percent |  |  |  |  |
| rc_predictor_velocity_hz |  |  |  |  |
| rc_predictor_time |  |  |  |  |
| fpv_mix_degrees |  |  |  |  |
| yaw_around_gravity |  |  |  |  |
| max_aux_channels |  |  |  |  |
| serialrx_provider |  |  |  |  |
| serialrx_inverted |  |  |  |  |
| spektrum_sat_bind |  |  |  |  |
| spektrum_sat_bind_autoreset |  |  |  |  |
| srxl2_unit_id |  |  |  |  |
| srxl2_baud_fast |  |  |  |  |
| sbus_baud_fast |  |  |  |  |
| crsf_use_rx_snr |  |  |  |  |
| airmode_start_throttle_percent |  |  |  |  |
| rx_min_usec |  |  |  |  |
| rx_max_usec |  |  |  |  |
| serialrx_halfduplex |  |  |  |  |
| msp_override_channels_mask |  |  |  |  |
| rx_spi_protocol |  |  |  |  |
| rx_spi_bus |  |  |  |  |
| rx_spi_led_inversion |  |  |  |  |
| show_altered_rc |  |  |  |  |
| adc_device |  |  |  |  |
| adc_vrefint_calibration |  |  |  |  |
| adc_tempsensor_calibration30 |  |  |  |  |
| adc_tempsensor_calibration110 |  |  |  |  |
| input_filtering_mode |  |  |  |  |
| blackbox_sample_rate |  |  |  |  |
| blackbox_device |  |  |  |  |
| blackbox_disable_pids |  |  |  |  |
| blackbox_disable_rc |  |  |  |  |
| blackbox_disable_setpoint |  |  |  |  |
| blackbox_disable_bat |  |  |  |  |
| blackbox_disable_mag |  |  |  |  |
| blackbox_disable_alt |  |  |  |  |
| blackbox_disable_rssi |  |  |  |  |
| blackbox_disable_gyro |  |  |  |  |
| blackbox_disable_acc |  |  |  |  |
| blackbox_disable_debug |  |  |  |  |
| blackbox_disable_motors |  |  |  |  |
| blackbox_disable_gps |  |  |  |  |
| blackbox_mode |  |  |  |  |
| min_throttle |  |  |  |  |
| max_throttle |  |  |  |  |
| min_command |  |  |  |  |
| dshot_idle_value |  |  |  |  |
| dshot_burst |  |  |  |  |
| dshot_bidir |  |  |  |  |
| dshot_bitbang |  |  |  |  |
| dshot_bitbang_timer |  |  |  |  |
| use_unsynced_pwm |  |  |  |  |
| motor_pwm_protocol |  |  |  |  |
| motor_pwm_rate |  |  |  |  |
| motor_pwm_inversion |  |  |  |  |
| motor_poles |  |  |  |  |
| motor_output_reordering |  |  |  |  |
| thr_corr_value |  |  |  |  |
| thr_corr_angle |  |  |  |  |
| failsafe_delay |  |  |  |  |
| failsafe_off_delay |  |  |  |  |
| failsafe_throttle |  |  |  |  |
| failsafe_switch_mode |  |  |  |  |
| failsafe_throttle_low_delay |  |  |  |  |
| failsafe_procedure |  |  |  |  |
| failsafe_recovery_delay |  |  |  |  |
| failsafe_stick_threshold |  |  |  |  |
| align_board_roll |  |  |  |  |
| align_board_pitch |  |  |  |  |
| align_board_yaw |  |  |  |  |
| gimbal_mode |  |  |  |  |
| bat_capacity |  |  |  |  |
| vbat_max_cell_voltage |  |  |  |  |
| vbat_full_cell_voltage |  |  |  |  |
| vbat_min_cell_voltage |  |  |  |  |
| vbat_warning_cell_voltage |  |  |  |  |
| vbat_hysteresis |  |  |  |  |
| current_meter |  |  |  |  |
| battery_meter |  |  |  |  |
| vbat_detect_cell_voltage |  |  |  |  |
| use_vbat_alerts |  |  |  |  |
| use_cbat_alerts |  |  |  |  |
| cbat_alert_percent |  |  |  |  |
| vbat_cutoff_percent |  |  |  |  |
| force_battery_cell_count |  |  |  |  |
| vbat_display_lpf_period |  |  |  |  |
| vbat_sag_lpf_period |  |  |  |  |
| ibat_lpf_period |  |  |  |  |
| vbat_duration_for_warning |  |  |  |  |
| vbat_duration_for_critical |  |  |  |  |
| vbat_scale |  |  |  |  |
| vbat_divider |  |  |  |  |
| vbat_multiplier |  |  |  |  |
| ibata_scale |  |  |  |  |
| ibata_offset |  |  |  |  |
| ibatv_scale |  |  |  |  |
| ibatv_offset |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
