+++
title = "Advanced Usage"
description = "Cockpit advanced usage documentation."
date = 2023-11-23T20:15:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
aliases = ['/software/control-station/Cockpit-latest/advanced-usage']

[extra]
lead = ''
toc = true
top = false
+++

## Display Breakdown

{{ easy_image(src="interface-overview", width=650, center=true) }}

### Header Bar

The header bar consists of the following main elements:

#### Burger Menu

Clicking on the burger menu (in the top left of the screen) provides access to various 
[configuration](#configuration) options:

{{ easy_image(src="burger-menu", width=300, center=true) }}

#### Mission Name

It is possible to set a display name for the current mission/operation from beside the burger menu. If the name
is deleted it can be made available again by visiting the [Mission Planning](#mission-planning) page.

#### Alerts

Alerts received from the autopilot ([`STATUSTEXT`](https://mavlink.io/en/messages/common.html#STATUSTEXT)), as
well as application notifications (like loss of connection to the vehicle) are displayed in the central alerts
pane, which can be hovered over to access a scrollable history of alerts:

{{ easy_image(src="alert-history", width=450, center=true) }}

Some alerts can be read aloud on arrival using text to speech technology, which [can be configured](#alerts).

#### Mini Widget Container

When space is available, [mini widgets](#mini-widgets) can be placed on the right side of the alerts display.

#### Date

The current time and date is displayed in the top right corner.

## Edit Mode

Cockpit's interface is designed around a configurable widget system, within an arbitrary set of views.
Widgets can be added/removed, placed in arbitrary locations, and resized.

{{ easy_image(src="edit-mode", width=650, center=true) }}

### Views

A "view" is like a page that [widgets](#widgets) can be displayed in. It is possible to configure multiple
separate views and switch between them during operation, which is useful if you have different interface
preferences for when you're performing different operations.

As an example, you may have one view tailored to general navigation, and another that's designed around
inspections. The first view could then be used while getting the vehicle to the inspection site, and then
the second view can be switched to once it's time to actually perform the inspection.

If a vehicle is not always controlled through the same control station computer/device then it may be useful
to configure different views for the best control experience with each device.

It is possible for different devices or browser instances to access Cockpit at the same time (e.g. using
separate browser profiles, or one display in incognito mode, but currently **not** multiple tabs of the same
browser instance), with their views configured independently. To use the same component layouts across
instances you can export the desired view(s) from one and import into the other(s).

Multiple simultaneous tabs from the same browser instance will be supported in future.

#### Configuration

- Open edit mode via the [burger menu](#burger-menu)
- Select a view to edit, and/or create or remove views as desired
    - Views can be imported from an external file, or exported to a file for sharing
- The "Current widgets" list allows
    1. dragging the widgets in the current view to reorder which widget is on top
        - This helps for use-cases like overlaying a HUD element on a video display
    1. removing an existing widget from the current view
    1. resizing a widget to fill the entire view
- New widgets can be added via the bottom section
    - Clicking on a regular widget adds it to the view, after which it can be positioned and resized as desired
    - Mini widgets have fixed sizes, but can be dragged and dropped into the desired location in the header/footer
      bars or in a [mini widget bar](#mini-widget-bar)
- Some regular widgets can be configured, by clicking the three dots in the top right corner of the widget
- Mini widgets that support configuration can be clicked on anywhere on the widget to open the configuration options
    - This is currently only possible during operation, *not* while in edit mode

### Widgets

There are several types of widgets available, and in future it will be possible to create, import, and use custom widgets as well.

#### Regular Widgets

##### Attitude HUD

The attitude HUD widget displays the vehicle's pitch and roll as a heads-up display overlay:
{{ easy_image(src="attitude-hud-widget", width=300, center=true) }}

It is possible to configure which components get displayed, as well as the line colour:
{{ easy_image(src="attitude-hud-config", width=500, center=true) }}

##### Virtual Horizon

The virtual horizon widget displays the vehicle's pitch and roll as though on the gauge in a plane:
{{ easy_image(src="virtual-horizon-widget", width=300, center=true) }}

It is most useful for guided and/or autonomous control, where the main display is of the vehicle's position.

##### Compass

The compass widget displays the vehicle's orientation as though looking at a compass in your hand:
{{ easy_image(src="compass-widget", width=300, center=true) }}

It is most useful for guided and/or autonomous control, where the main display is of the vehicle's position.

It is possible to configure the vertical direction to be fixed to North ("North-up") or to the vehicle's 
forwards direction ("head-up").
{{ easy_image(src="compass-config", width=300, center=true) }}

##### Compass HUD

The compass HUD is a first-person compass view, as though inside a compass and looking in the direction the
vehicle is pointing (its heading):
{{ easy_image(src="compass-hud-widget", width=600, center=true) }}

It is possible to configure whether the exact heading angle is shown, whether to use a -180 to +180° range
(default is 0 to 360°), and the colour of the lines:
{{ easy_image(src="compass-hud-config", width=500, center=true) }}

##### Depth HUD

The depth HUD indicates the vehicle's current depth as determined by its external pressure sensor:
{{ easy_image(src="depth-hud-widget", width=200, center=true) }}

This is primarily useful for underwater vehicles.

Configuration determines whether the exact depth value is shown, and the colour of the lines:
{{ easy_image(src="depth-hud-config", width=500, center=true) }}

##### Indicators

The indicators widget shows a collection of telemetry values, including the vehicle's attitude, GPS location,
and optionally its power supply and usage and some debugging data: 
{{ easy_image(src="indicators-widget", width=200, center=true) }}
{{ easy_image(src="indicators-config", width=300, center=true) }}

##### Image Viewer

The image viewer widget shows an image that is accessible to the control station computer via its network.
{{ easy_image(src="image-viewer-config", width=400, center=true) }}

Images from the internet can be included (e.g. a logo for branding) as long as the computer has internet
access when Cockpit is started.

This is most useful for images hosted on the local network, and was designed to display the output of a
self-replacing mjpeg like from an ESP32-Cam. It could also display images hosted by a
[BlueOS Extension](https://blueos.cloud/docs/blueos/latest/extensions).

##### Map

For vehicles with a positioning system, the map widget displays the 
[registered home location](https://mavlink.io/en/messages/common.html#MAV_CMD_DO_SET_HOME) and the vehicle's
[current position](https://mavlink.io/en/messages/common.html#GLOBAL_POSITION_INT), with an option to track
the vehicle's path over time.

There are buttons to 
1. move the map to follow the registered 'home' location
    - this may move around if the control station computer is on a boat
1. move the map to follow the vehicle's current position
1. download the current mission from the vehicle, and display it on the map
1. execute the mission that is on the vehicle
{{ easy_image(src="map-widget", width=350, center=true) }}
{{ easy_image(src="map-config", width=350, center=true) }}

In future it will be possible to set the current vehicle position, and click to guide the vehicle to new
positions.

##### Video Player

The video player widget displays an available WebRTC video stream. BlueOS uses the 
[MAVLink Camera Manager](https://github.com/mavlink/mavlink-camera-manager) to automatically create a WebRTC 
stream for applicable video streams.
{{ easy_image(src="video-widget", width=400, center=true) }}

Multiple video widgets can be added to display different video streams.

Configuration allows selecting which video stream to display, flipping the stream image, and choosing how
the frames should fit within the widget:
- **cover**: maintains the video aspect ratio, but expands the frames to fully cover the widget, and crops
off the sides or top+bottom if they extend beyond the widget boundaries
- **fill**: stretches the frames so that all sides are against the corresponding widget boundary
- **contain**: maintains the video aspect ratio, but shrinks the frames to fully fit inside the widget,
adding transparent padding at the sides / above+below as necessary
{{ easy_image(src="video-config", width=600, center=true) }}

It is also possible to select the video source IP, which is recommended especially if there are multiple
available connection routes (e.g. if there is a wired route through a tether, as well as a wireless connection,
you should select the tether IP and remove the wireless one to avoid video stuttering from transmission over wifi).

Video recording is possible using a [mini widget](#mini-widgets), and directly records the incoming stream
(not the scaled and cropped display of the widget).

##### Mini Widget Bar

The mini widget bar widget is a rectangular container for storing [mini widgets](#mini-widgets).

{{ easy_image(src="mini-widgets-bar-widget", width=500, center=true) }}

#### Mini Widgets

Mini widgets are small, generally single-function widgets that can be drag-positioned in the
[header bar](#header-bar), footer bar, or any [mini widget bar](#mini-widget-bar).

They are editable by selecting "Mini Widgets" in the bottom left corner of edit mode, then either
dragging a new mini-widget (from those available along the bottom of the screen) into a
[mini-widget bar](#mini-widget-bar), or configuring or removing one from the "current mini-widgets"
list in the bottom left corner.

The current options include
- Arm/Disarm toggle switch
- Vehicle connection status indicator
- Power / battery indicator
- Depth indicator
- (Relative) altitude indicator
- Very generic indicator
    - configuring this allows selecting which vehicle variable to track, out of
      any that have been received so far (including custom ones)
    - only variables coming from Ardupilot vehicles are currently supported
    - available variables include those comming from `NAMED_VALUE_FLOAT/INT` messages as well
      as any variable that is inside any MAVLink message
    - several pre-made presets are available for usage with common variables
    - it is also possible to specify a display unit, a value multiplier, an icon, the number of
      digits after the decimal place and a custom display name
{{ easy_image(src="very-generic-widget-config-presets", width=300, center=true) }}
{{ easy_image(src="very-generic-widget-config-custom", width=300, center=true) }}
- Video recorder
    - allows recording one of the available WebRTC streams, or the full Cockpit tab
    - recording occurs in the browser of the display device (not onboard the vehicle)
        - this is currently stored in memory and downloaded to the device when finished, which may limit
        maximum time for individual recordings
    - recordings are saved using the [mission name](#mission-name) and the starting timestamp
- Joystick connection status indicator
- Flight mode selector
- GPS status indicator
- [View](#views) selector

## Configuration

Cockpit's behaviour can be configured via the [burger menu](#burger-menu), with the following tabs:

### General

Connection configuration allows specifying custom endpoint addresses for Cockpit to communicate with.
When Cockpit is hosted by a vehicle running BlueOS these are usually correct by default, but if using
it standalone or connecting to some external services it may be necessary to specify different
addresses, and refresh the page to establish the desired connection.

{{ easy_image(src="../getting-started/general-config", width=600, center=true) }}

### Joysticks

Cockpit is intended to work with arbitrary joystick types, and allows mapping joystick buttons and axes
to [`BTNn_FUNCTION`](https://docs.bluerobotics.com/ardusub-zola/software/autopilot/ArduSub-4.1/developers/parameters/#btnn-function-function-for-button)
values for use in regularly sent [`MANUAL_CONTROL`](https://mavlink.io/en/messages/common.html#MANUAL_CONTROL)
MAVLink messages, as well as to Cockpit Actions which can send commands to the vehicle or trigger interface
events like like view switching or starting a video recording.

{{ easy_image(src="../getting-started/joystick-config", width=600, center=true) }}

Support is built in for simultaneous input from multiple sources, including multiple joysticks, and by
default each joystick can provide up to 8 axis ranges and 32 buttons. As some caveats,

- ArduSub only supports 16 independent buttons and 4 axis ranges in its `MANUAL_CONTROL` handling
- When mapping the Z motion axis range, note that ArduSub uses 0 to +1000 for full reverse to full forwards,
whereas other vehicle types use -1000 to +1000
- Cockpit can assign a button to the "Shift" `BTNn_FUNCTION`, but is not currently capable of mapping
a secondary "shifted" autopilot action to its other buttons
    - This currently needs to be set up separately, either directly using vehicle parameters, or using
    an alternative control station software like QGroundControl
- Cockpit is currently only capable of mapping to `BTNn_FUNCTION` values that have already been assigned to
a button, which may need to be done in advance using parameters or QGroundControl

Adding support for a new joystick type requires providing an SVG file with particular element IDs
(for function mapping, and so the elements can be dynamically filled when the corresponding button is pressed):
- `path_b*` is used for different button numbers, numbers can currently be from 0-31
    - the buttons can be remapped during Cockpit configuration by clicking on the displayed button in the SVG
    display and clicking the "Remap" button followed by pressing the actual joystick button that matches the
    displayed location
- `path_b10`/`b11` are currently used to denote the joystick axes
    - 10 indicates the left side joystick, 11 indicates the right side one
    - in future there will be support for arbitrary axes and sliders
- New SVGs currently need to be added to the code, but in future will be possible to add/import dynamically

### Alerts

It is possible to select the desired text-to-speech voice, as well as configure which alert severities
are read out loud:

{{ easy_image(src="alert-config", width=600, center=true) }}


## Mission Planning

- Allows planning (and saving/loading) autonomous missions
- Allows mission control

{{ easy_image(src="mission-planning", width=600, center=true) }}
