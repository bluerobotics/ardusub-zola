+++
title = "Getting Started"
description = "Cockpit getting started instructions."
date = 2023-12-12T22:20:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 20
draft = false
aliases = ['/software/control-station/Cockpit-latest/getting-started']

[extra]
lead = ''
toc = true
top = false
+++
## General Configuration

When run as a BlueOS Extension, Cockpit will automatically be configured to connect using the IP address of the connection to BlueOS.

If that address changes during operating (or if Cockpit is run as a standalone application) it may be necessary to configure the
global vehicle address, MAVLink2REST address, and WebRTC signalling server address so that Cockpit knows the correct connection 
points for the vehicle. After address configuration it is necessary to refresh the page.

To access the configuration section, open the burger menu in the top left, and select "Configuration".

{{ easy_image(src="general-config", width=500, center=true) }}

## Interface Setup

### Visual Display
By default, the interface of Cockpit is set up with three [views](../advanced-usage/#views):
1. Video view
    - Includes a video stream, vehicle telemetry, compass and attitude instrument indicators, status updates, and flight mode selection
    - Useful for first-person control of a vehicle like an ROV, copter, or plane, focused on what the vehicle can see

{{ easy_image(src="video-view", width=600, center=true) }}

2. HUD view
    - Includes a video stream, vehicle telemetry, heads-up display (HUD) overlay elements, status updates, and flight mode selection
    - An alternative for first-person control of a vehicle like an ROV, copter, or plane, focused on precision maneuvering

{{ easy_image(src="hud-view", width=600, center=true) }}

3. Map view
    - Includes a map, vehicle telemetry, status updates, and flight mode selection
    - Most useful for mission planning and remote monitoring of vehicles with a positioning system and/or autonomous control

{{ easy_image(src="map-view", width=600, center=true) }}

The available views and the widgets within them (including sizing and placement) can be configured as described in the
[advanced usage documentation](../advanced-usage/#edit-mode).

### Joystick Configuration
For vehicles controlled via a joystick, button and axis mappings can be set by clicking the burger menu (top left), then selecting
"Configuration" and navigating to the Joystick tab.

{{ easy_image(src="joystick-config", width=500, center=true) }}

## Vehicle Setup

Cockpit does not currently contain vehicle configuration or calibration functionalities. It is recommended to perform these in advance,
using either the BlueOS web interface and/or an alternative control station software like QGroundControl.

It is possible to switch between Mission Planning and Flight displays via the burger menu in the top left.
