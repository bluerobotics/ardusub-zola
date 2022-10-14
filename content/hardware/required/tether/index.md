+++
title = "Tether"
description = "Provides low latency high-bandwidth communication between the onboard computer and the control station, which other technologies are poorly suited to."
date = 2022-10-11T17:33:19+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 45
draft = false
[extra]
lead = ""
toc = true
top = false
+++

A tether is a length of cable which connects the [Onboard Computer](../onboard-computer/) to the [Topside Computer](../control-computer/). Radio frequency (RF) waves do not travel far through water and acoustic modems have limited bandwidth, so a tether is a critical component to connect the vehicle to a surface computer.

## Requirements

The Onboard Computer communicates with 10/100/1000 Base Ethernet. If 10/100 Base is acceptable, a standard [Cat 5 cable](https://en.wikipedia.org/wiki/Category_5_cable) may be used to connect to the vehicle and topside computer. The maximum transmission length of Cat5 cable is around 100m.

{{ easy_image(src="tether", width=300) }}

Alternative tether types (twisted pair, fiber optic, etc) and lengths require a [Tether Interface](../../recommended/tether-interface/).
