## RF Tap

<p align="center">
<img src="./img/MeasurementSetup.jpg" width="1000" height="600"/>
</p> 

## Credits

* Wes Hayward W7ZOI and Bob Larkin W7PUA for great base design of RF Tap described in QST June 2001 issue.
* Barry L. Dorr for detailed analysis of resistive pi attenuator design.
* Fesz (owner of Fesz Electronics youtube channel) for great hints regarding how to match ltspie simulations to NanoVNA measurements - You rock Fesz!!!

## Design Overview
RF Tap is a device used to extract or monitor radio frequency (RF) signals from a transmission line without significantly disturbing the original signal. The RF signal at Tap output is attenuated to a level that is safe for measurement equipment such as oscilloscope. In case of this particular design attenuation is fixed to -40dB (voltage at RFTap output is x100 lower then one, which is present at the transmission path). All three RF Tap terminals have 50ohm impedance.
This design is based on work by Wes Hayward W7ZOI and Bob Larkin W7PUA described in [1]. The only modification made here is the use of precission potentiometer instead of one of the resistors used to attenuate RF signal for precise attenuation level adjustment.

Circuit Schematics:

<p align="center">
<img src="./schematics/RF_Tap_Schematics.png" width="400" height="300"/>
</p>

Resistors R1a, R1b and R1c shall be 500mW rated. R2 can be 125mW rated. Please note that if you do not terminate RF path with 50ohm dummy load or antenna, power (Prms) dissipated on one of R1 resistors goes up to 1.3W!

Calculations of resistor values for given level of attenuation:

<p align="center">
<img src="./docs/PrinciplesOfOperations.png" width="500" height="900"/>
</p>

## Circuit Simulations

To be able to relate simulation results to NanoVNA measurements the first step is to establish measurement correction, which Nanovna calculates as part of calibration process.

<p align="center">
<img src="./sim/S21CalibrationResult.png" width="400" height="400"/>
</p>

As can be seen from the results above, in our case the calibration correction is +6dB, which is added to all measurement results.

Now we can simulate RF Tap attenuation levels for unterminated and terminated with 50ohm resistor RF Paths:

<p align="center">
<img src="./sim/S21SimulationResults.png" width="1000" height="700"/>
</p>

In case of unterminated RF Path attenuation of RF Tap is equal -34dB and when the RF Path is terminated with 50ohm load attenuation increases to -40dB. 

As can be seen in Measurements section simulation results match perfectly actual measurements.

Simulation of the impact of parasitic capacitance present in the circuit and effect of corrective capacitance added in parallel to resistor R1 can be found below:

<p align="center">
<img src="./sim/S21SimulationResults_FrequencyDependingLoss.png" width="1000" height="700"/>
</p>

Finally, calculations of resistor power ratings is given below (simulation run for peak power value of 100W):

<p align="center">
<img src="./sim/ResistorPowerRatingSimulation.png" width="1000" height="700"/>
</p>

## Measurements

### Device frequency response measured between one of RF path ends and RF tap output (another RF path end is terminated with 50ohm dummy load)

<p align="center">
<img src="./meas/S21_RF_Input_RF_Tap_noCap_50ohmTerm_2024-03-03 11-27-41.png" width="400" height="400"/>
<img src="./meas/S21_RF_Input_RF_Tap_withCap_50ohmTerm.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's S21 curve when capaitor C is present. 
Picture to the left shows Tap's S21 curve when capacitor C is not present. 
The cap C reduces attenuation for signals above 144MHz.

### VSWR measured at one of RF path ends (another RF path end is terminated with 50ohm dummy load)

<p align="center">
<img src="./meas/VSWR_RF_Input_noCap_50ohmTerm_2024-03-03 11-19-03.png" width="400" height="400"/>
<img src="./meas/VSWR_RF_Input_RF_Tap_withCap_50ohmTerm_2024-03-03 12-27-44.png" width="400" height="400"/>
</p>

Picture to the right shows RF Tap's VSWR curve measured at RF input for device with capaitor C.
Picture to the left shows Tap's VSWR curve measured at RF input for device with no capacitor C.
In both cases other end of RF path is terminated with 50 ohm dummy load.
It can be observed that while capacitor C improves Tap's frequency response seen from Tap output (attenuation is closer to -40dB accross enntire band) it also slightly increases VSWR measured at one of RF path ends.


### Insertion loss measured at RF path ends (RF Tap termination does not impact measurements)

<p align="center">
<img src="./meas/S21_RF_Input_RF_Input_noCap_2024-03-03 11-49-04.png" width="300" height="300"/>
</p>

Insertion loss caused by RF Tap is not greater then -0.5dB accross entire band (DC-500MHz). Presence of Cap does not impact insertion loss level in any significant way.
RF Tap termination does not impact measurement results i.e. insertion loss is the same for RF Tap output terminated with 50ohm resistor and when RF Tap is left open.

## References

[1] "Simple RF-Power Measurement", QST June 2001 by Wes Hayward W7ZOI and Bob Larkin W7PUA

[2] "Ten Essential Skills for Electrical Engineers" by Barry L. Dorr, Willey 2014, Chapter: "How to Design Resistive Circuits"