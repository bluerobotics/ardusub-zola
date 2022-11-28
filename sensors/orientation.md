+++
title = "Inertial"
description = "Inertial orientation/motion sensor types."
date = 2022-11-21T21:50:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false

[extra]
lead = "Inertial sensors make measurements of the vehicle orientation and motion without requiring direct access to the surrounding environment"
toc = true
top = false
+++

## Sensors

### Sensor Types

Type | Subtype(s) | Primary Function(s) | Interface Library
---|---|---|---
Accelerometer | motion<br>/ orientation | translation<br>/ uprightness | ...
Magnetometer<br>/ Compass | motion<br>/ orientation | yaw rate<br>/ angle | ...
Gyroscope | motion<br>/ orientation | rotation rate<br>/ roll/pitch/yaw changes | ...
Barometer (external) | positioning<br>/ motion | depth<br>/ vertical | ...
Barometer (internal) | safety | ... | ...
Temperature | environment | accuracy correction | ...
Power Usage | safety | battery level<br>/ usage within capacity | ...
Rangefinder<br>/ Altimeter | positioning<br>/ safety | terrain-follow<br>/ target tracking<br>/ obstacle avoidance | ...
Leak Detector | safety | enclosure failure | ...
GPS (surface) | positioning | absolute localisation<br>/ drift correction | ...
USBL / SBL | positioning | ... | ...
DVL | positioning | positioning | ...

### Tested with ArduSub

Sensor | Type | [Used On](@/hardware/required/autopilot/index.md) | Integration Source
---|---|---|---
[MMC5983](.) | Magnetometer | Navigator | ...
[AK09915](.) | Compass | Navigator | ...
[LSM303D](.) | Accel / Mag | Pixhawk | ...
[IST8310](.) | Magnetometer | Pixhawk 4 | ...
[ICM-20602](.) | IMU | Navigator / Pixhawk 4 | [AP_IntertialSensor_Invensense.cpp](https://github.com/ArduPilot/ardupilot/blob/Sub-4.1/libraries/AP_InertialSensor/AP_InertialSensor_Invensense.cpp)
[L3GD20H](.) | Gyroscope | Pixhawk | ...
[MPU6000](.) | accel/gyro | Pixhawk | ...
[BMI055](.) | accel/gyro | Pixhawk 4 | ...
[ICM-20689](.) | accel/gyro | Pixhawk 4 | ...


### Magnetometers / Compasses

- Measure magnetic field strength in all directions
- Can estimate North orientation by strongest magnet direction
- Calibration allows correcting for _constant_ magnetic effects from vehicle components
- Subject to error due to magnetic field fluctuations (from nearby changing electrical currents, and going near large magnetic structures)
- DIFFERENCE??
- [`AP_...` library](.)

### Gyroscopes

- Measure rotation rate about all axes
- Can be integrated over time to estimate relative rotation angles
   - Integrated readings continually build error, and need to be corrected for by an absolute reference
- Faster response than compass
- [`AP_...` library](.)
- [`AP_Compass` library](https://github.com/ArduPilot/ardupilot/tree/master/libraries/AP_Compass)

### Accelerometers

- Measure acceleration in all directions
- Can directly estimate gravity direction
- Can be integrated over short time periods to estimate "airspeed" (speed through the transport fluid)
   - Integrated readings continually build error, and need to be corrected for by an absolute reference, or not used
- Can be doubly-integrated to estimate position relative to a starting time
   - Double integration error grows exponentially, so is impractical to use without frequent corrections
- [`AP_InertialSensor` library](https://github.com/ArduPilot/ardupilot/tree/master/libraries/AP_InertialSensor)

### Tested with ArduSub

## Code Usage
InertialSensor -> InertialNav / NavEKF/2/3 -> AHRS -> AttitudeControl

