+++
title = "Control Station (Topside) Computer"
description = "Sends operator input to the vehicle, and receives and displays information from the vehicle."
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

The Control Station Computer is the operator's primary interface to their vehicle(s). In subsea applications it is often referred to as the Topside Computer or Surface Computer, whereas for rovers and aerial vehicles it is normally called the Ground Control Station (GCS) Computer.

When controlling an ArduSub vehicle, the Topside Computer is tethered to the [Onboard Computer](../onboard-computer/). The vehicle is controlled using Control Station software such as the QGroundControl application, which displays the live video feed and telemetry data to the operator, and accepts piloting inputs from a connected [joystick](../joystick) for manual control.

## Supported Operating Systems

QGroundControl has been tested and is supported on the following operating systems:

* Windows 10 - 64 bit
* macOS 10.20 or later
* Ubuntu 18.04 or later

The minimum recommended hardware for running QGroundControl is:

* i5 processor or better
* 8GB RAM
* Solid-state hard drive (SSD)

### Consumer Level Computers

QGroundControl runs well on consumer level laptops meeting the minimum specifications in the section above. These types of laptops are generally made to be used indoors, so they lack bright screens and water resistance for use outside. If possible, try to find a computer with the brightest screen possible. The engineering department of Blue Robotics uses this [Dell XPS 15 laptop](https://www.dell.com/en-us/shop/dell-laptops/new-xps-15-laptop/spd/xps-15-7590-laptop/XNber5cr656Ps?view=configurations&configurationid=55d274d4-e828-4110-b161-3acaa604d481) as of 2020.

### Rugged and Semi-Rugged Computers

If a brighter screen or water resitance are required, then a rugged or semi-rugged laptop may be a better choice. Modern rugged laptops are about equal with their consumer level counterparts from a performance perspective.

* [Panasonic Toughbook Series](https://na.panasonic.com/us/computers-tablets-handhelds)
* [Dell Rugged Series](https://www.dell.com/en-us/work/learn/rugged)
* [Getac Laptops and Tablets](https://www.getac.com/)

### Custom Computers

With the introduction of the ArduSub system and compatibility with major operating systems, users are building their own topside computer systems, usually into ruggedized travel cases. A high brightness screen (>1000 nits) is installed in the lid and the computer components are located into the remainder of the case. 

Below is an example of such a case from Blue Link:

{{ easy_image(src="topside-computer-bluelink", width=400) }}

## Unsupported Operating Systems

Althugh QGroundControl can be downloaded onto these operating systems, ArduSub is not currently supported on:

* Android
* iOS
