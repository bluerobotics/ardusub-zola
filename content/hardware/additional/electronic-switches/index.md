+++
title = "Electronic Switches (Relays and MOSFETs)"
description = "Enables the autopilot and/or onboard computer to control higher voltage (>5V DC) and high power circuits via software."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 35
draft = false
[extra]
lead = ""
toc = true
top = false
+++


Electronic switches are useful for turning higher voltage (>5V DC) auxiliary equipment on and off via digital outputs on the autopilot board. Most commonly they use relay or MOSFET components.

Up to four electronic switches can be operated via joystick button functions when connected to the appropriate signal outputs.

Most autopilots cannot provide power to the output rail to trigger the relays, so a [5V power supply](https://bluerobotics.com/store/comm-control-power/elec-packages/bec-5v6a-r1/) will need to be connected to an empty output.



