+++
title = "Electronic Switches (Relays and MOSFETs)"
description = "Enables the autopilot and/or onboard computer to control higher voltage (>5V DC) and high power circuits via software."
date = 2023-03-10T01:10:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 35
draft = false
[extra]
lead = ""
toc = true
top = false
+++


Electronic switches are useful for turning higher voltage (>5V DC) / high power auxiliary equipment on and off via digital outputs on the [flight controller board](../../required/flight-controller/). Most commonly they use relay or MOSFET components.

Up to four electronic switches can be operated via the "relay" joystick button functions when connected to the appropriate signal outputs.

Most flight controllers cannot provide power to the output rail to trigger the relays, so a [5V power supply](https://bluerobotics.com/store/comm-control-power/elec-packages/bec-5v6a-r1/) will generally need to be connected to the AUX power connector (if it exists), or to the power pin on one of the outputs.
