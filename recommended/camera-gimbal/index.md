+++
title = "Camera Tilt Mount / Gimbal"
description = "Used to move and/or stabilise the camera, for smoother video feeds and looking around without needing to rotate or move the whole vehicle."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
[extra]
lead = ""
toc = true
top = false
+++


ArduSub supports control and attitude atabilization for up to 3-axis gimbals. The most common gimbal type for underwater vehicles is a 1-axis tilt mount, since the majority of standard ROV frames have control over the other Degrees of Freedom (DoF).

ArduSub supports both simple servo-driven (PWM) gimbals in which the autopilot's onboard IMU controls the stabilisation and brushless direct drive (UART) gimbals that have their own self-stabilization controllers.

## Supported Camera Gimbals

{{ easy_image(src="cam-mount" width=300) }}

The following gimbals are supported in ArduSub:
* [Servo Gimbals](https://bluerobotics.com/store/sensors-sonars-cameras/cameras/camera-tilt-mount/)
* [Gremsy Pixy U](https://ardupilot.org/copter/docs/common-gremsy-pixyu-gimbal.html#common-gremsy-pixyu-gimbal) 
* [SimpleBGC (aka AlexMos) Gimbal Controller](https://ardupilot.org/copter/docs/common-simplebgc-gimbal.html#common-simplebgc-gimbal)
* [SToRM32 Gimbal Controller](https://ardupilot.org/copter/docs/common-storm32-gimbal.html#common-storm32-gimbal) (communicates with MAVLink)
