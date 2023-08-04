+++
title = "Electronic Speed Controllers (ESCs)"
description = "Used to control the speed/thrust of motors and thrusters."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 25
draft = false
[extra]
lead = ""
toc = true
top = false
+++

ArduSub is designed to work with brushless and brushed Electronic Speed Controllers (ESCs) to control motors and [thrusters](../thrusters/). Different motor types require different ESCs, so the ESCs must match the motor type they are being used to control.

ArduPilot does not support controlling both brushed and brushless motors at the same time.

The minimum requirements for an ESC of either type are:

* Bi-directional control - they operate in forward and reverse (most ESCs for UAVs and hobby drones only operate in one direction)
* Controlled by a PWM input where:
    * 1900 us is full forward
    * 1500 us is stopped
    * 1100 us is full reverse

## Brushless ESCs

{{ easy_image(src="besc" width=500) }}

The following brushless ESCs are supported for use with ArduSub:

* [Blue Robotics Basic ESC](https://bluerobotics.com/store/thrusters/speed-controllers/besc30-r3/)
* [Blue Robotics Basic ESC 500](https://bluerobotics.com/store/thrusters/speed-controllers/besc500/)

There is a comparison of properties [in the Blue Robotics Technical Reference](https://bluerobotics.com/learn/technical-reference/#speed-controllers-escs).

## Brushed ESCs

No brushed ESCs have been reported to be used with ArduSub, but here is the reference documentation from ArduPilot:

* [Brushed Motor ESCs](https://ardupilot.org/rover/docs/common-brushed-motors.html)
