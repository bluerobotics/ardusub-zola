+++
title = "Overview"
description = "Cockpit overview."
date = 2023-05-16T21:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
aliases = ['/software/control-station/Cockpit-latest/overview']

[extra]
lead = 'Cockpit is an intuitive and customizable cross-platform control station software for remote vehicles of all types.'
toc = true
top = false
+++

## A bit of context...

The existing market for control station software is missing an option that's readily available, easy to use, versatile, easy to customise and develop for, and cross-platform. In response to this need, and fueled by years of inspirations for what a truly great control station could be, Cockpit is Blue Robotics' next-generation control interface, for thrusting your vehicle control experience into the future.

## Availability

Cockpit is currently publicly available [as a BlueOS Extension](https://docs.bluerobotics.com/BlueOS-Extensions-Repository#:~:text=Cockpit,-Maintainer) (requires BlueOS >= 1.1). It is still in an initial development phase, and will not be actively supported until it is officially released.

## Primary Feature List

- Browser-based control station software, for vehicle control and monitoring from any web-capable device
- Widget-based layout system, with freeform and grid-snapped positioning and resizing options
- Widget layers, for saved collections of interface elements
- Custom display "views", for interface pages/profiles that can be switched between
    - Views can contain multiple widget layers
    - Different browser windows/screens/devices can independently select which view to display
    - Views will be shareable in future
- WebRTC-based video widget
    - Multiple widgets can be added to support arbitrary numbers of video streams
    - Includes video recording support, on the display device
- Map widget
    - Provides position tracking
    - Allows planning autonomous missions
- Customisable Actions mappable to user inputs (e.g. joysticks, key presses, screen clicks)
    - Actions can send commands to the vehicle, or can trigger local events like interface changes and starting video recording
    - Includes support for simultaneous input from multiple sources (including multiple joysticks)
- Joysticks of _any_ type can be configured and calibrated
    - Buttons and axes can be mapped to arbitrary Actions
