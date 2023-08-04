+++
title = "Other Sensors (Temperature, Salinity, Thickness, etc)"
description = "Can be helpful for research, or estimating related phenomena (e.g. sound speed for sonar and acoustic positioning performance)."
date = 2023-03-15T20:00:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 15
draft = false
[extra]
lead = ""
toc = true
top = false
+++

A variety of other sensors types can be useful in a marine environment, for research and/or to measure phenomena that improve the accuracy of other sensors and vehicle control. Sensors that may be of interest include

- [conductivity](https://discuss.bluerobotics.com/t/using-conductivity-sensor-with-brs-flight-controller-and-qgc/13126)
- hydrophones
- [O2, salinity](https://discuss.bluerobotics.com/t/o2-and-salinity-sensors/2569)
- [pH](https://discuss.bluerobotics.com/t/ph-sensor-recommendations/13197)
- [sediment and water samplers](https://discuss.bluerobotics.com/t/water-sampler-sediment-sampler/2712)
- temperature
- [ultrasonic thickness gauge](https://discuss.bluerobotics.com/t/cygnus-ultrasonic-thickness-gage/2967)

## Temperature Sensor

An auxiliary external temperature sensor may be added for obtaining faster and more accurate readings than those from an integrated pressure sensor. Duplicate sensors are not supported (e.g. two of the same temperature sensor at different locations on the vehicle).

ArduSub has a pre-installed driver for the following sensor type:

* [Measurement Specialties TSYS01](https://www.te.com/commerce/DocumentDelivery/DDEController?Action=showdoc&DocId=Data+Sheet%7FTSYS01%7FA%7Fpdf%7FEnglish%7FENG_DS_TSYS01_A.pdf%7FG-NICO-018)


## Supported Sensor Products

{{ easy_image(src="celsius", width=350) }}

The following sensor products may be directly connected to an [autopilot](../../required/flight-controller-boards/):
* [Celsius Fast-Response, ±0.1°C Temperature Sensor (I2C)](https://bluerobotics.com/store/sensors-sonars-cameras/sensors/celsius-sensor-r1/)
* [PCB for Celsius Fast-Response, ±0.1°C Temperature Sensor](https://bluerobotics.com/store/sensors-sonars-cameras/sensors/celsius-sensor-pcb-r1/)
