+++
title = "Advanced Usage"
description = "Cockpit advanced usage documentation."
date = 2023-12-13T01:30:00+11:00
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

It is possible to set a display name for the current mission/operation from beside the burger menu.

A default mission name is randomly selected each time Cockpit is opened/restarted. The default names are not
used for saving files/recordings, but modified names are. While modifying the mission name it is possible
to restore the previous name (e.g. if you change you mind or make a mistake).

{{ easy_image(src="mission-name-config", width=450, center=true) }}

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

Cockpit's interface consists of a configurable widget system, with
1. [Profiles](#profiles)
    - for supporting different operators and/or vehicle types
    - can be added/removed/duplicated, saved and loaded (to/from both the vehicle and the display device),
    and switched between in edit mode
1. [Views](#views) (within each profile)
    - for handling different operation modes / targets within a mission
    - can be added/removed/duplicated, saved and loaded to/from the display device, and
    dynamically switched between during operation
1. [Widgets](#widgets) (within each view)
    - for advanced information display and vehicle control
    - can be added/removed, placed in arbitrary locations, and resized
1. [Mini-widgets](#mini-widgets) (within mini-widget bar widgets)
    - for basic information display and vehicle/interface control
    - can be added/removed, reordered within widget bars, and moved between them

{{ easy_image(src="edit-mode", width=650, center=true) }}

### Profiles

A "profile" is a collection of [views](#views) that are relevant to a particular use-case or operator.

If one control station computer is used by multiple operators (e.g. within the same organisation)
at different times then it could be useful for each operator to have their preferred interface saved on
that computer, and they can switch to their profile when they open up Cockpit.

Alternatively, if the same control station computer is used to control different types of vehicles
(e.g. a boat, an underwater ROV, and a drone) then the operator can load the appropriate vehicle control
interface when they connect to a different vehicle type. It will soon be possible to store and load
profiles from the vehicle itself, instead of only on the control station computer, which makes it easier
to connect a different control computer to a vehicle and load the familiar control profiles for that vehicle.

#### Default Profiles

Cockpit includes default profiles for submarine and boat use-cases. It is possible to restore to these
(as a known reasonable interface) in case something goes wrong with your custom profiles, but be aware
that the defaults may change between different Cockpit versions, so may end up restoring to an interface
you haven't seen before.

#### Profile Configuration

1. Open edit mode (via the [burger menu](#burger-menu)
1. Select a custom/user profile to edit, and/or create, import, or remove profiles as desired
    - Profiles can be renamed by clicking on the settings cog icon, or duplicated via the copy icon
    - Additional profiles can be imported from the display device or the connected vehicle
        - Opening Cockpit on a new device will automatically try to load profiles from the vehicle
        - If the browser already has Cockpit profiles stored, it will not try to load any from the
          vehicle unless the import from vehicle button is clicked
    - The set of available profiles can be stored onto the vehicle, or reset/restored to the defaults
        - Storing profiles onto the vehicle overwrites those that may already be there
    - The "Views" list shows the views that are available within the selected profile

### Views

A "view" is like a page that [widgets](#widgets) can be displayed in. It is possible to configure multiple
separate views and switch between them during operation, which is useful if you have different interface
preferences for when you're performing different operations.

As an example, you may have one view tailored to general navigation, and another that's designed around
inspections. The first view could then be used while getting the vehicle to the inspection site, and then
the second view can be switched to once it's time to actually perform the inspection.

It is possible for different devices or browser instances to access Cockpit at the same time (e.g. using
separate browser profiles, or one display in incognito mode, but currently **not** multiple tabs of the same
browser instance), with their views configured independently. To use the same component layouts across
instances you can export the desired view(s) from one and import into the other(s).

Multiple simultaneous tabs from the same browser instance will be supported in future.

#### Configuration

- Open edit mode via the [burger menu](#burger-menu)
- Select a view to edit, and/or create or remove views as desired
    - Views can be imported from an external file, or exported to a file for sharing
    - Clicking on the cog settings icon allows renaming a view, and determining whether the footer bar is
      shown or hidden/docked when Cockpit boots
        - It is always possible to toggle the current footer bar visibility using
          [Cockpit Actions](#cockpit-actions) (e.g. via a joystick button)
{{ easy_image(src="view-config", width=250, center=true) }}
- The "Current widgets" list allows
    1. dragging the widgets in the current view to reorder which widget is on top
        - This helps for use-cases like overlaying a HUD element on a video display
    1. removing an existing widget from the current view
    1. resizing a widget to fill the entire view
- New widgets can be added via the bottom section
    - Clicking on a regular widget adds it to the view, after which it can be positioned and resized as desired
    - Mini widgets have fixed sizes, but can be dragged and dropped into the desired location in the header/footer
      bars or in a custom [mini widget bar](#mini-widget-bar)
    - The selector in the bottom left can be used to choose between editing regular or mini widgets
- Some widgets can be configured, by clicking the cog settings icon in the "Current widgets" list
    - [There are currently cog icons for all widgets](https://github.com/bluerobotics/cockpit/issues/541),
      so if you click a cog icon and nothing happens it means that widget is not configurable

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

##### IFrame

The iframe widget provides an inline frame that can display another HTML page within the Cockpit interface.
This is particularly useful for showing the interfaces and displays of BlueOS Extensions (e.g. for a sonar viewer):
{{ easy_image(src="iframe-widget", width=400, center=true) }}

Configuration determines the URL to fetch the page from, as well as the overall transparency of the iframe:
{{ easy_image(src="iframe-config", width=400, center=true) }}

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
A warning is provided when multiple routes are available:

{{ easy_image(src="video-multiple-ip-warning", width=400, center=true) }}

Video recording is possible using a [mini widget](#mini-widgets), and directly records the incoming stream
(not the scaled and cropped display of the widget). Cockpit can be configured to 
[log some telemetry values](#logs), and record them as a subtitle file for convenient video playback:

{{ easy_image(src="video-subtitles", width=450, center=true) }}

##### URL Video Player

The URL video player widget displays a video from a URL. This is useful for testing IP cameras that are not
being redirected via BlueOS, but can also be used to display online videos if that is for some reason relevant.
{{ easy_image(src="url-video-widget", width=400, center=true) }}

Configuration allows selecting which URL to stream a video from, as well as options for whether to play the
video automatically, whether it should loop when complete, whether it should play sound or be muted, whether
playback controls should be exposed, and choosing how the video frames should fit within the widget (as
described in [Video Player](#video-player).
{{ easy_image(src="url-video-config", width=450, center=true) }}

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
    - a warning is displayed if Cockpit is closed while a video is recording, and a recovery popup
    appears when Cockpit is next opened in that browser / on that device
{{ easy_image(src="video-recording-config", width=250, center=true) }}
{{ easy_image(src="video-recording-termination-warning", width=400, center=true) }}
{{ easy_image(src="video-recording-recovery", width=400, center=true) }}
- Joystick connection status indicator
- Flight mode selector
- GPS status indicator
- [View](#views) selector
- Takeoff/land button

## Configuration

Cockpit's behaviour can be configured via the [burger menu](#burger-menu), with the following tabs:

### General

Connection configuration allows specifying custom endpoint addresses for Cockpit to communicate with.
When Cockpit is hosted by a vehicle running BlueOS these are usually correct by default, but if using
it standalone or connecting to some external services it may be necessary to specify different
addresses, and refresh the page to establish the desired connection.

{{ easy_image(src="../getting-started/general-config", width=600, center=true) }}

### Joysticks

Cockpit is intended to work with arbitrary joystick types, and allows mapping joystick buttons and axes to
various [protocol functions](#joystick-protocols), which can send inputs and commands to the vehicle, or trigger
interface events. Once a function mapping is configured it is possible to export it to the computer and/or the
vehicle, which can then be imported later to new Cockpit instances/devices.

{{ easy_image(src="../getting-started/joystick-config", width=600, center=true) }}

Support is built in for simultaneous input from multiple sources, including multiple joysticks, and by
default each joystick can provide up to 8 axis ranges and 32 buttons.

#### Joystick Protocols

When mapping the functionality of a joystick button or axis, there are multiple protocols to choose from:

{{ easy_image(src="joystick-button-mapping", width=500, center=true) }}

##### MAVLink `MANUAL_CONTROL` Messages

[`MANUAL_CONTROL`](https://mavlink.io/en/messages/common.html#MANUAL_CONTROL) MAVLink messages are 
automatically sent to the vehicle at 25Hz, which is not currently configurable.

Button functions are determined by the autopilot firmware - e.g. in ArduSub they correspond to
[`BTNn_FUNCTION`](https://docs.bluerobotics.com/ardusub-zola/software/autopilot/ArduSub-4.1/developers/parameters/#btnn-function-function-for-button)
parameter values.

As a few caveats:
- ArduSub <= 4.1.x only supports 16 independent buttons and 4 axis ranges in its `MANUAL_CONTROL` handling
    - More recent versions support the extended protocol, with 32 buttons and 6 motion axis inputs
- ArduRover does not support buttons via the `MANUAL_CONTROL` protocol
- When mapping the Z (vertical) motion axis range, note that ArduSub uses 0 to +1000 for full reverse to full
  forwards, whereas other vehicle types use -1000 to +1000

The function mapping decision process is designed to minimise intrusiveness to existing setups. When mapping a
`MANUAL_CONTROL` button function to a joystick button, Cockpit
1. First tries to use already mapped functions
    - e.g. if there is already a `BTNn_FUNCTION` configured to enable Stabilize mode, a Cockpit button being set
      to enable Stabilize mode will map to that existing function bit
1. Then overwrites available Disabled `BTNn_FUNCTION`s
1. Then tries to overwrite any mapped function bits that Cockpit currently isn't using
    - If you try to change a Cockpit function to a `MANUAL_CONTROL` function when there are no buttons left it
      will display an error message about insufficient buttons

It is permitted to map the joystick button functions without a vehicle connected, in which case any relevant
autopilot parameters will be automatically remapped once the vehicle connects. If more `MANUAL_CONTROL` button
functions have been assigned than are supported by the vehicle then the extra ones are removed, and a warning
is raised to notify that the configured mapping is not fully as designed.

##### Cockpit Actions

Joystick buttons can also be configured to run more general functionalities, like modifying the interface or
sending a single MAVLink message. The current supported Actions are:

- `go_to_next_view`
- `go_to_previous_view`
- `toggle_bottom_bar`
- `toggle_full_screen`
- `mavlink_arm`
- `mavlink_disarm`

##### Modifier Keys

Modifiers allow sacrificing one button in order to add an extra functionality slot for every non-modifier button.
Pressing a button while a modifier is held runs the modified function instead of the regular button function.

Currently only a single modifier is available (Shift). As a special case, when a shift functionality slot is
configured as a MAVLink `MANUAL_CONTROL` protocol function, it will activate `BTNn_SFUNCTION`s rather than the
regular `BTNn_FUNCTION`s, which allows additional `MANUAL_CONTROL` button functions to be configured. Functions
from other joystick protocols are unaffected, and can be arbitrarily assigned to regular or modifier-based
functionality slots.

##### Other

Currently only used for the "No Function" option.

#### Custom Joysticks

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

Once Cockpit has a suitably registered SVG file for the desired joystick type, it is possible to perform the
relevant "Joystick mapping", from the button IDs presented by the physical joystick to labels that match the
corresponding buttons in the SVG file. This mapping can then be exported to the computer and/or the vehicle,
and imported to new Cockpit instances/devices later.

## Logs

Cockpit can optionally record some of its received telemetry values, which can then be turned into subtitle
files when recording videos. 

Currently the possible variables for logging are pre-defined, and the output format is determined automatically.
If left unconfigured, the variables that are recorded by default are those from active widgets in the selected 
[Profile](#profiles). It is possible to override which variables are logged via the configuration page, but
custom widgets like the `VeryGenericIndicator` cannot currently be logged.

{{ easy_image(src="logging-config", width=600, center=true) }}

Logging is at a fixed rate of 1Hz. When a video recording completes, a corresponding subtitle file is generated
by slicing the raw log from the start to end timestamps of the video.

{% note() %}
Recorded video and subtitles are in separate files, so the browser will typically ask for permission to "download
multiple files", which must be accepted to get access to the subtitles corresponding to a video recording.
{% end %}

### Alerts

It is possible to select the desired text-to-speech voice, as well as configure which alert severities
are read out loud:

{{ easy_image(src="alert-config", width=600, center=true) }}

## Mission Planning

- Allows planning (and saving/loading) autonomous missions
- Allows mission control

{{ easy_image(src="mission-planning", width=600, center=true) }}
