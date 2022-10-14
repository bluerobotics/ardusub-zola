+++
title = "Thrusters"
description = "Used to maneuver a vehicle in marine environments. The number and orientation of thrusters on a vehicle determines the degrees of freedom (DoF) it may maneuver in."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
[extra]
lead = ""
toc = true
top = false
+++

Thrusters are necessary to maneuver an underwater vehicle around. The number and orientation of thrusters on a vehicle determines the number of degrees of freedom (DoF) it may maneuver in.

The maximum current draw of the power supply on the vehicle is an important consideration when choosing what type and how many thrusters to mount on a vehicle. The maximum current draw at the intended voltage should be totaled up for all the thrusters. If this exceeds the current rating of the power supply, either lower the supply voltage, [limit the maximum thrust](https://discuss.bluerobotics.com/t/raspberry-and-pixhawk-shutdown-problem/10814/2), or remove thrusters.

ArduSub can be used with both brushless and brushed thrusters, but all motion-control thrusters on a single vehicle must use the same type of control signal, and each thruster needs to be paired to an [Electronic Speed Controller (ESC)](../esc/) that matches its motor type.

## Brushless Thrusters

Brushless thrusters are a good choice for propulsion as they do not have brushes that must be protected or wear out. 

## Recommended Brushless Thrusters

{{ easy_image(src="t200" height=300) }}

The following brushless thrusters have been tested and are recommended for use:

* [Blue Robotics T200 Thruster](https://bluerobotics.com/store/thrusters/t100-t200-thrusters/t200-thruster-r2-rp/)
* [Blue Robotics T500 Thruster](https://bluerobotics.com/store/thrusters/t100-t200-thrusters/t500-thruster/)

There is a comparison of properties [in the Blue Robotics Technical Reference](https://bluerobotics.com/learn/technical-reference/#thrusters).

## Brushed Thrusters

Brushed thrusters are generally cheaper than brushless types, but must be internally sealed with either an oil compensating system or have shaft seals.

Partially disasembled bilge pump motors with propellers have been used in the past for a shallow water sealed thruster unit.

Brushed thrusters must use an appropriate [brushed ESC](../esc/#brushed-escs).
