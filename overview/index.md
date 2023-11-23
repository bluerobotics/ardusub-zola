+++
title = "Overview"
description = "Cockpit overview."
date = 2023-11-23T17:00:00+11:00
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

{{ easy_image(src="cockpit-banner", width=460, center=true) }}

{{ easy_image(src="interface-highlight", width=650, center=true) }}

## A bit of context...

The existing market for control station software is missing an option that's readily available, easy to use, versatile, easy to customise and develop for, and cross-platform. In response to this need, and fueled by years of inspirations for what a truly great control station could be, Cockpit is Blue Robotics' next-generation control interface, for thrusting your vehicle control experience into the future.

## Availability

Cockpit is currently publicly available [as a BlueOS Extension](https://docs.bluerobotics.com/BlueOS-Extensions-Repository#:~:text=Cockpit,-Maintainer) (requires BlueOS >= 1.1). It is still in an initial development phase, and will not be actively supported until it is officially released.

The source code is available [on GitHub](https://github.com/bluerobotics/cockpit),
under [two possible licenses](https://github.com/bluerobotics/cockpit/tree/master/LICENSE.md).

## Primary Feature List

- Browser-based control station software, for vehicle control and monitoring from any web-capable device
- Widget-based layout system, with freeform positioning and resizing
- Custom display [Views](../advanced-usage/#views), for interface pages/profiles that can be switched between
    - Different browser windows/screens/devices can independently select which view to display
    - Views are downloadable and can be shared (json contains name and list of components and widget settings)
- MAVLink `NAMED_VALUE_FLOAT`/`_INT` messages are self-registering for use in [mini-widgets](../advanced-usage/#mini-widgets) (including custom ones!)
- WebRTC-based [video widget](../advanced-usage/#video)
    - Multiple widgets can be added to support arbitrary numbers of video streams
    - Includes video recording support, on the display device
- [Map widget](../advanced-usage/#map)
    - Provides position tracking
    - Allows planning (and saving/loading) autonomous missions
    - Allows mission control
    - In future will allow setting the current vehicle position, and clicking to guide the vehicle to new positions
- Customisable Actions mappable to user inputs (e.g. joysticks, and key presses / screen clicks in future)
    - Actions can send commands to the vehicle, or can trigger local events like view switching and starting video recording
    - Includes support for simultaneous input from multiple sources (including multiple joysticks)
- [Joysticks](../advanced-usage/#joysticks) of _any_ type can be configured
    - Buttons and axes can be mapped to arbitrary Actions
- [Notification system](../advanced-usage/#alerts)
    - Displays autopilot (MAVLink `STATUSTEXT`) and application alerts
    - Includes text to speech announcements
- [Mission naming](../advanced-usage/#mission-name) used on the interface and video save filenames
