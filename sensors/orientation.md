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

### Magnetometers / Compasses

- Measure magnetic field strength in all directions
- Can estimate North orientation by strongest magnet direction
- Calibration allows correcting for _constant_ magnetic effects from vehicle components
- Subject to error due to magnetic field fluctuations (from nearby changing electrical currents, and going near large magnetic structures)
- DIFFERENCE??
- [`AP_...` library]()

### Gyroscopes

- Measure rotation rate about all axes
- Can be integrated over time to estimate relative rotation angles
   - Integrated readings continually build error, and need to be corrected for by an absolute reference
- Faster response than compass
- [`AP_...` library]()
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
- [MMC5983 magnetometer]() (Navigator)
- [AK09915 compass]() (Navigator)
- [LSM303D accel/mag]() (Pixhawk)
- [IST8310 magnetometer]() (Pixhawk 4)
- [ICM-20602 IMU]() (Navigator / Pixhawk 4)
- [L3GD20H gyro]() (Pixhawk)
- [MPU6000 accel/gyro]() (Pixhawk)
- [BMI055 accel/gyro]() (Pixhawk 4)
- [ICM-20689 accel/gyro]() (Pixhawk 4)
- [ICM 20602](https://github.com/ArduPilot/ardupilot/blob/master/libraries/AP_InertialSensor/AP_InertialSensor_Invensense.cpp)


## Code Usage
InertialSensor -> InertialNav / NavEKF/2/3 -> AHRS -> AttitudeControl

