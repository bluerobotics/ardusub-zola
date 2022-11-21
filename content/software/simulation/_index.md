+++
title = "Simulation"
description = "Documentation for simulating an ArduSub vehicle."
date = 2022-11-21T18:40:00+11:00
template = "docs/section.html"
sort_by = "weight"
weight = 50
draft = false
+++

- SITL simulates the autopilot, and some very basic physics
   - SITL should run on BlueOS, although it currently doesn't have the right parameters
- Gazebo and BlueSim are more advanced physics and operations simulators and the first person interface, but don't simulate the autopilot
- QGroundControl allows user input to the running simulation, and provides a map/missions interface
- MAVLink inputs can be from a program (see programatic-control)
