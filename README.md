## RF Tap

<p align="center">
<img src="./img/MeasurementSetup.jpg" width="1000" height="600"/>
</p> 

## Credits

* Wes Hayward W7ZOI and Bob Larkin W7PUA for great base design of RF Tap described in QST June 2001 issue.

## Design Overview

## Circuit Simulations

## Measurements

# Frequency response of measured between on of the RF inputs and RF tap output

<p align="center">
<img src="./meas/S21_RF_Input_RF_Tap_noCap_50ohmTerm_2024-03-03 11-27-41.png" width="400" height="400"/>
<img src="./meas/S21_RF_Input_RF_Tap_withCap_50ohmTerm.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's S21 curve when capaitor C is present. The cap C reduces attenuation for signals above 144MHz.
Picture to the left shows Tap's S21 curve when capacitor C is not present. 

<p align="center">
<img src="./meas/VSWR_RF_Input_noCap_50ohmTerm_2024-03-03 11-19-03.png" width="400" height="400"/>
<img src="./meas/VSWR_RF_Input_RF_Tap_withCap_50ohmTerm_2024-03-03 12-27-44.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's VSWR curve measured at RF input for device with capaitor C.
Picture to the left shows Tap's VSWR curve measured at RF input for device with no capacitor C.
In both cases other end of RF path is terminated with 50 ohm dummy load.
It can be observed that while capacitor C improves Tap's frequency response seen from Tap output (attenuation is closer to -40dB accross enntire band) it also slightly increases VSWR measured at one of RF path ends.


<p align="center">
<img src="./meas/S21_RF_Input_RF_Input_noCap_2024-03-03 11-49-04.png" width="300" height="300"/>
</p>

Insertion loss caused by RF Tap is not greater then -0.5dB accross entire band.

## References

[1] "Simple RF-Power Measurement", QST June 2001 by Wes Hayward W7ZOI and Bob Larkin W7PUA