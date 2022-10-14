+++
title = "Tether Interface"
description = "Converts an ethernet connection to a signal type more suited to long distances and different tether types."
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

Although optional and not necessary for basic functionality, tether interfaces increase the **range** and **reliability** of Ethernet communications.

## Interfaces for Copper Twisted Wire Pairs

Interface boards which use the [Homeplug AV](https://en.wikipedia.org/wiki/HomePlug#HomePlug_AV) standard provide a robust high-speed, long-distance Ethernet connection over a single pair of wires. These boards enable HD video and high-bandwidth data over 300m+ tether lengths.

{{ easy_image(src="fathomx" width=350) }}

The following interface boards are supported:
* [Blue Robotics Fathom-X Tether Interface Board Set](https://bluerobotics.com/store/comm-control-power/tether-interface/fathom-x-r1/)

## Interfaces for Fiber Optic Cable

With communications being Ethernet based, fiber optic cables may also be used with Ethernet-to-Fiber converters installed inside the ROV and topside.

The following fiber optic interface boards have been known to work: 
* [DeltaROV Subsea Fiber to Ethernet Communication Kit](http://www.deltarov.com/new/product/drov-subsea-fiber-to-ethernet-communication-kit/)
