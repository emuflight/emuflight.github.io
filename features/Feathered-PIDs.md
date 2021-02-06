---
layout: default
title: Feathered PIDs
parent: Features
nav_order: 5
---

# Featherd PIDs

* Feathered PIDs changes how dTerm (kD) is calculated.
* 0 is error-based dTerm and 100 is measurement based-dTerm.
* dTerm based on error is how KISS calculates dTerm.
* dTerm on measurement is how BetaFlight calculates dTerm.
* Measurement-based is smoother but less responsive than error-based.
* Any value in-between is a percentage of each.
* Some quads prefer error-based, while others prefer measurement-based.
* 50 is an exact balance between both.