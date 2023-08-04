+++
title = "Leak Sensors"
description = "Detect and provide warning if a leak occurs, before it gets to and damages the electronics in an enclosure."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
[extra]
lead = ""
toc = true
top = false
+++

Leak sensors are an important addition for saving an electronics enclosure should a leak occur.

ArduSub can be configured to read leak sensors through auxiliary servo pins on a Pixhawk when set to GPIO mode, and the dedicated leak pins on a Navigator. A failsafe action can be configured to either send a warning or automatically surface the vehicle when a leak is detected.

## Supported Sensors

{{ easy_image(src="leak-sensor", width=200) }}

The following sensor products are supported:

* [Blue Robotics SOS Leak Sensor](https://bluerobotics.com/store/sensors-sonars-cameras/leak-sensor/sos-leak-sensor/)
