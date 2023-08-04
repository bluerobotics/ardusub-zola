+++
title = "Positioning Sensors (GPS / DVL)"
description = "Allows waypoint and target-based navigation, position holding, and location-tagged data collection."
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

A positioning system is a useful addition to an ArduSub vehicle either for displaying numerical location coordinates or the position of the vehicle on a map in QGroundControl. 

Below is an example of a Water Linked Underwater GPS System being used to locate a shipwreck:

<iframe frameborder="0" width=640 height=360 allow="autoplay" src="https://www.youtube.com/embed/NpAClMNhno0"></iframe>
<br><br>

{% note() %}
The [autopilot](/introduction/hardware-options/required-hardware/autopilot.md) has the capability of utilizing an external positioning system to perform autonomous maneuvers like station keeping, 'click to go here', transects, and pre-planned waypoint missions, however this is IN DEVELOPMENT.
{% end %}

## GPS Module

ArduSub maintains the same [GPS module drivers](https://ardupilot.org/copter/docs/common-positioning-landing-page.html) as the rest of the ArduPilot family of firmwares, so a compatible GPS module may be directly connected to the GPS port on the autopilot. Positioning information will only be available when the vehicle is on the surface and the module is out of the water. The module will not be able to obtain a fix if it is underwater due to high frequency radio waves being unable to penetrate the water medium.

Acoustic positioning systems are the only reliable way of providing positioning information underwater.

## SBL Positioning Systems

A [short baseline (SBL) acoustic positioning system](https://en.wikipedia.org/wiki/Short_baseline_acoustic_positioning_system) uses an acoustic transmitter on the vehicle to transmit timed acoustic pulses. These pulses are received by a series of multiple receivers on the surface in an arranged geometric pattern. The ["time of flight"](https://en.wikipedia.org/wiki/Time_of_flight) is calculated to when each receiver records the acoustic pulse and then a consolidated position for the underwater vehicle can be plotted.

SBL systems can produce better positioning accuracy in highly reflective environments due to the adjustable receiver locations.

{{ easy_image(src="SBL-WL", width=500) }}
<sup style="color:grey;">Image Credit: Water Linked</sup>

### Supported SBL Systems

* [Water Linked Underwater GPS Explorer Kit](https://store.waterlinked.com/underwater-gps/)

## USBL Positioning Systems

An [ultra-short baseline acoustic positioning system](https://en.wikipedia.org/wiki/Ultra-short_baseline) is similar to SBL system where an acoustic pulse is transmitted from a tranciever on the vehicle and then recieved by a receiver on the surface. Instead of simply calculating time of flight, range and bearing are calculated by USBLs.

USBLs are more compact than SBL systems where the receiver's transducers are fixed in one tranciever head.

{{ easy_image(src="USBL-CS", width=500) }}
<sup style="color:grey;">Image Credit: Cerulean Sonar</sup>

### Supported USBL Systems

* [Cerulean Sonar ROV Locator](https://ceruleansonar.com/products/rovl-mkii?variant=39414929915970)

## DVL Positioning Systems

A [doppler velocity log](https://en.wikipedia.org/wiki/Acoustic_Doppler_current_profiler#Bottom_tracking) sends multiple acoustic pulses in different directions, and measures the frequency change (doppler shift) from the transmitted pulses to estimate velocity of the vehicle relative to the bottom. Combining the velocity estimate with measurements from the accelerometers, compass, and gyroscopes in the onboard inertial measurement unit (IMU), the vehicle's orientation and relative position can be estimated via dead-reckoning. If the time of flight of the pulses is measured, it is also possible to estimate vehicle altitude above the bottom, similar to an [altimeter](../sonars/#echosounders-and-altimeters).

{{ easy_image(src="WL-DVL", height=300) }}
<sup style="color:grey;">Image Credit: Water Linked</sup>

DVLs do not require external acoustic hardware or infrastructure, so are better suited to long distance autonomous missions than an SBL or USBL system.

The relative positioning estimates from a DVL system mean the estimate is prone to drift over time. Accurate long term positioning requires occasional corrections from an absolute positioning system (like a GPS Module at the surface).

### Supported DVL Systems

* [Water Linked DVL-A50](https://store.waterlinked.com/product/dvl-a50/?hsCtaTracking=b79feacb-c824-4524-b3e0-2f6513163a7f%7C44cc28cf-75a8-4e25-ac64-ee6bc3e9e5e8)
* [Cerulean Sonar DVL-75](https://ceruleansonar.com/products/dvl-75?variant=32632308760642)
* [Teledyne Wayfinder](http://www.teledynemarine.com/Wayfinder)

There is a comparison of some common DVLs in [this forum comment](https://discuss.bluerobotics.com/t/dvl-recommendations/10775/2#comparisons-1).
