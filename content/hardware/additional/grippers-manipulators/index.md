+++
title = "Grippers and Manipulators"
description = "A gripper is a useful tool for picking up small objects, attaching recovery lines, or freeing a snagged tether. Other manipulators may be useful in cleaning, inspection, or repair tasks."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 40
draft = false
[extra]
lead = ""
toc = true
top = false
+++

A gripper is a useful tool for picking up small objects, attaching recovery lines, or freeing a snagged tether. Other manipulators may be useful in cleaning, inspection, or repair tasks.

Ardusub has the ability to natively control grippers through assigning joystick buttons and servo outputs for grippers that use Pulse Width Modulation (PWM) for control. Depending on the control circuitry, this may include momentary open/close actions, or precise position control.

Other grippers often have their own control software and interface for assigning control functions. Grippers which use RS485 for control can use a spare twisted wire pair in the tether for data transmission, whereas grippers with RS232 control require custom software on the [Companion Computer](/introduction/hardware-options/required-hardware/companion-computer.md).

## Supported Grippers and Manipulators

{{ easy_image(src="gripper", width=500) }}

The following grippers have been used on ArduSub vehicles:

* [Blue Robotics Newton Subsea Gripper](https://bluerobotics.com/store/rov/bluerov2-accessories/newton-gripper-asm-r2-rp/) (PWM output from autopilot)
* [Blueprint Lab Series Grippers](https://blueprintlab.com/products/grabbers/) (RS485 through the tether)
