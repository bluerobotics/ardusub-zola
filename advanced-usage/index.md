+++
title = "Advanced Usage"
description = "BlueOS advanced usage documentation."
date = 2023-03-08T12:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
aliases = ['/software/onboard/BlueOS-latest/advanced-usage', '/blueos/latest/advanced-usage']

[extra]
lead = ''
toc = true
top = false
link_base = "https://github.com/bluerobotics/BlueOS-docker/tree/1.1.0-beta.16/core"
+++

## General Information

This documentation page is for detailed information about the services and pages
in the BlueOS web interface. For a higher level list and direct comparison of
features see the [Overview](../overview/#feature-comparison) instead.

### Pirate Mode

The default BlueOS interface is simplified, and shows only the major tools that
most people are likely to find useful. Full functionality is available via 
"Pirate Mode", which can be enabled from the [header bar](#display-mode-management).
Note that Pirate Mode is advanced/development mode, and should be used with care.

This documentation by default shows the full functionality interface, to provide
an overview of _all_ functionality instead of a limited subset, but if you're only
interested in the basic functionality you can click the button below:

<div style="text-align:center;padding-bottom:15px;">
<!-- functionality code at bottom of file -->
<button onclick="toggle_advanced()" id="pirate_toggle">
    hide advanced functionality
</button>
</div>

For clarity of this documentation, any pages that are extended by (or only available
in) Pirate Mode are shown in [dark mode](#display-mode-management), and described
with grey text.

### Interface Overview
{{ service(service="blueos-frontend", port=80) }}

When you first open BlueOS, you'll see a window like the following:
{{ easy_image(src="interface-overview", width=600) }}

#### Header: Indicators and BlueOS Configuration

On the right side of the header you'll find:
##### Notifications
- Press broom to clear notifications
- Press cog to toggle showing old messages

{{ easy_image(src="notifications", width=350) }}

##### Ethernet + static IP management
{{ service(service="Cable Guy", port=9090, link="/services/cable_guy", based=true) }}

Choose between:
- A static IP
- A dynamic IP
- A DHCP server

{{ easy_image(src="ethernet", width=350) }}

##### Wifi + Hotspot network management
{{ service(service="Wifi Manager", port=9000, link="/services/wifi", based=true) }}

- Choose a wifi network to connect to
   - The BlueOS web interface is accessible via 
   [http://blueos-wifi.local](http://blueos-wifi.local) when
   connected to the same wifi network as your device (including a mobile phone)

{{ easy_image(src="wifi", width=350) }}

- Forget, connect to, or a force a new password for a saved network

{{ easy_image(src="wifi-example", width=250) }}

- Configure or turn on/off the BlueOS wireless hotspot, or display a QR code to
easily connect to it from a phone
   - The hotspot SSID is named `BlueOS (******)` by default, where the asterisk
   field varies for each system
      - The default password for the hotspot is `blueosap`
   - The BlueOS web interface is accessible via 
   [http://blueos-hotspot.local](http://blueos-hotspot.local) and
   [http://192.168.42.1](http://192.168.42.1) when your device is connected to
   the BlueOS hotspot network

{{ easy_image(src="hotspot-example", width=250) }}

##### Display Mode Management

- [Pirate mode](#pirate-mode) can be toggled via the happy robot /
skull-and-crossbones icon
   - Access or hide advanced functionality
   - **Advanced users only** - pirate mode is not recommended for normal use
- Light and dark display modes can be toggled between with the sun / moon icon

{{ easy_image(src="display-mode", width=250) }}

##### System status
- Heartbeat icon pulses with vehicle heartbeat, and goes red if heartbeat is lost
- On click shows onboard computer temperature, voltage, and current usage
- Additional warning icons appear if a problem is detected on the onboard computer:
   - High disk usage
   - CPU overheating
   - CPU throttling
   - CPU under voltage
   - Connected wirelessly (instead of through a tether)
{{ easy_image(src="system-status", width=200) }}

#### Sidebar

The burger menu at the top left of the header opens up the sidebar, for
conveniently accessing available pages, tools, and services. When the page
is wide enough, the sidebar automatically stays open.

{{ simple_pirate_image(src="sidebar", width=200) }}

##### BlueOS Settings

{{ easy_image(src="settings", width=300) }}

- Reset BlueOS settings
   - Remove existing camera/endpoint/bridges configuration
- Remove log files from BlueOS services (to reduce space usage on the SD card)
- Download log files from BlueOS services to report a problem
  - Old logs are aggregated and kept as zip files

##### Power

{{ simple_pirate_image(src="power", width=300) }}

- Power off
   - Shut down onboard computer
   - Recommended before turning off vehicle power
- Reboot
   - Reboot onboard computer
{% simple() %}
- Soft restart
   - Do a software-restart of BlueOS (without restarting the computer)
   - Generally sufficient for most 'reboot' requirements
{% end %}
{% pirate() %}
- Restart core container (same as "Soft restart")
   - Restart the core BlueOS docker container
   - Generally sufficient for most 'reboot' requirements
{% end %}

##### Feedback

{{ easy_image(src="feedback", width=300) }}

Submit feedback about BlueOS via:
- [Issues on the GitHub repository](https://github.com/bluerobotics/BlueOS-docker/issues)
   - allows easily tracking changes, 
and notification when complete/fixed
- Posts on [the Blue Robotics forum](https://discuss.bluerobotics.com)
   - allows easy discussion with the community

### Dashboard
The "Dashboard" page provides an overview of the available pages. In future it
will provide an overview of the vehicle state and main configuration options.

{{ simple_pirate_image(src="dashboard", width=600) }}

## Tools
Pages in the "Tools" section provide access to data or allow interaction with the system.

{% pirate() %}
### Available Services

The Available Services page provides developer access to the underlying http
server interfaces of the services upon which BlueOS is based. Each service is
listed with 
- the port it is served at
- a meaningful name
- a web-page link using the active 
[network configuration](../getting-started/#interface-access)

and where relevant
- its API documentation (in a live-testable form)
- the current API version

Any service that provides an http server with a
[title tag](https://www.w3schools.com/tags/tag_title.asp) will be displayed.
Documentation can also be parsed if
- it follows the swagger/open api spec, and 
- is available at `/docs` or `/v1.0/ui`
{% end %}
{{ easy_image(src="available-services", width=600, class="pirate") }}

{% pirate() %}
### Bag Editor
{% end %}
{{ service(service="Bag of Holding", port=9101, link="/services/bag_of_holding", based=true) }}
{% pirate() %}

The Bag Editor is a helper service for advanced users, which allows modifying the
database used to handle frontend interface changes.
{% end %}
{{ easy_image(src="bag-editor", width=600, class="pirate") }}

{% pirate() %}
### File Browser
{% end %}
{{ service(service="File Browser", port=7777, link="https://github.com/filebrowser/filebrowser") }}
{% pirate() %}

The File Browser allows viewing, editing, downloading, and uploading BlueOS files.

{% end %}
{{ easy_image(src="file-browser", width=600, class="pirate") }}

### Log Browser
{{ service(service="UAV LogViewer", link="https://ardupilot.org/copter/docs/common-uavlogviewer.html") }}

- Allows downloading telemetry `.bin` logs from Linux-based autopilots
   - Set the `BRD_RTC_TYPES` autopilot parameter to include `MAVLINK_SYSTEM_TIME`
   so the filenames use timestamps
- Can stream logs from external flight controllers (e.g. Pixhawks) if the
`LOG_BACKEND_TYPE` autopilot parameter is set to `MAVLink`
   - [May be inconsistent](https://github.com/bluerobotics/BlueOS-docker/issues/457)

{{ easy_image(src="log-browser", width=600) }}

- Press the green play button to access the built in Log Viewer, to visualise and
analyse vehicle telemetry (including position if a positioning system is equipped)
{{ easy_image(src="log-viewer", width=600) }}

{% pirate() %}
### MAVLink Inspector
{% end %}
{{ service(service="MAVLink2Rest", port=6040, link="https://github.com/patrickelectric/mavlink2rest") }}
{% pirate() %}

The MAVLink Inspector provides real-time access to the MAVLink messages being
sent to the topside computer. It is possible to
- filter for particular messages
- view past and current messages
- click on messages to see their full details
{% end %}
{{ easy_image(src="mavlink-inspector", width=600, class="pirate") }}
{% pirate() %}
Future improvements will include plotting and comparisons, along with more
powerful filtering options.

For tracking the latest value of a single message type, use the "watcher"
functionality of the `MAVLink2REST` service (access via the
[Available Services](#available-services) page).
{% end %}

### Network Test
{{ service(service="Pardal", port=9120, link="/services/pardal", based=true) }}

The Network Test page measures real-time latency between BlueOS and the surface
computer, and allows checking the upload and download speeds between them.

A plot is provided of each test, to help diagnose intermittent issues.

{{ easy_image(src="network-test", width=600) }}

### System Information
{{ service(service="System Information", port=6030) }}

The System Information page provides useful information about the processes,
network configuration, and computer system BlueOS is running on. It can be
useful for troubleshooting, and finding if a particular program is using
excessive resources.
{{ easy_image(src="system-info-processes", width=600) }}
{{ easy_image(src="system-info-monitor", width=600) }}
{{ easy_image(src="system-info-network", width=600) }}
{{ easy_image(src="system-info-kernel", width=600, class="pirate") }}
{{ easy_image(src="system-info-firmware", width=600, class="pirate") }}
{{ easy_image(src="system-info-about", width=600) }}

{% pirate() %}
### Terminal
{% end %}
{{ service(service="ttyd" link="https://tsl0922.github.io/ttyd/", port=8088) }}
{% pirate() %}

The Terminal provides
- A tmux session
   - Can split horizontally (`CTRL+b "`) and vertically (`CTRL+b %`), and use cursor
   to resize the panels
   - For more advanced tips, check out the
   [tmux cheat sheet website](https://tmuxcheatsheet.com/)
- Direct access into the core BlueOS docker container
- Ready access to the tmux sessions of the core services (`CTRL+b s`)
   - Useful for seeing logs as they update live
   - Can kill services if necessary
- Access to the underlying device via the `red-pill` utility
   - Can return to the core container using the `exit` command, or pressing `CTRL+d`
   - Can list available docker images (including extensions) with `docker image list`
   - Can list active docker containers (including extensions) with `docker ps -a`
{% end %}
{{ easy_image(src="terminal", width=600, class="pirate") }}

## Settings
Pages in the "Settings" section allow you to configure and update the system.

### Autopilot Firmware
{{ service(service="ArduPilot Manager", port=8000, link="/services/ardupilot_manager", based=true) }}

The Autopilot Firmware page provides basic information about the active
autopilot, along with options to:
{% pirate() %}
- Change board (select a connected board, or run an 
[SITL](https://www.ardusub.com/developers/sitl.html) simulation)
- Start the autopilot
- Stop the autopilot
{% end %}

- Restart the autopilot
- Update the firmware
   - [ArduPilot](https://ardupilot.org) family of [firmwares](https://firmware.ardupilot.org) only
   - Choose firmware to install
      - Select from the online repository
         - Select vehicle type (Sub / Rover / Plane / Copter)
         - Select desired release and stability level
            - Stable - A production-ready release.
               - The latest Stable is recommended for most users.
               - e.g. `Stable-4.1.1`
            - Beta - In-testing release, with new features and improvements, aiming
            to become stable. May have bugs.
            - Dev - Development branch, with all the newest features. Intentionally
            unstable (changes quickly), and possible untested/dangerous.
      - Upload a custom firmware file from the surface computer
      - Restore the default (ArduSub) firmware for the connected flight controller
   - Flash firmware onto a connected compatible
   [flight controller board](@/hardware/required/flight-controller/index.md)

{{ simple_pirate_image(src="firmware", width=600) }}

{% pirate() %}
Systems with a 
[Navigator](https://bluerobotics.com/store/comm-control-power/control/navigator/)
flight controller also have the option to configure serial-compatible ports from
the onboard computer (including USB ports) as serial ports accessible to the
autopilot.
{% end %}

{{ easy_image(src="firmware-serial", class="pirate", width=600) }}

### Autopilot Parameters
`New in 1.1`

The Autopilot Parameters page allows checking and changing the autopilot's configuration.

- Includes fuzzy searching of names and descriptions, to help find relevant parameters
- Allows loading parameters from a file, and saving the current parameters to a file

{{ easy_image(src="parameters" width=600) }}

### BlueOS Version

{{ service(service="Version Chooser", port=8081, link="/services/versionchooser", based=true) }}

The Version Chooser is a major component in the robust backbone of BlueOS. It
runs independently from the main interface, and is monitored such that if it
somehow fails a backup version will be run in its place.

{{ simple_pirate_image(src="version-chooser", width=600) }}

- The simplified interface provides an easy way to update to the latest version
that is [as stable or more stable](../overview/#release-types) than the currently installed version
{% pirate() %}
- The full interface supports easily changing forwards _and backwards_ between
versions
   - Previously-installed versions are kept locally on the device, unless
   manually deleted, which provides an easy route for roll-backs to undesired
   changes (e.g. during development)
- Allows loading remote versions (including from custom docker-hub repositories)
- Allows manually uploading docker images from the surface computer
- If an undetected failure somehow occurs in BlueOS (or if a broken version gets
installed) it's possible to easily roll back to a working version from
   - on the device
   - manual upload, or
   - downloaded from the internet
- If necessary, the underlying service can be accessed directly
   - e.g. [http://blueos.local:8081](http://blueos.local:8081)
{% end %}

{% pirate() %}
### MAVLink Endpoints
{% end %}
{{ service(service="ArduPilot Manager", port=8000, link="/services/ardupilot_manager", based=true) }}
{% pirate() %}

The MAVLink Endpoints manager allows configuring the serial, UDP, and TCP
endpoints for MAVLink-based services and programs to access.
{% end %}
{{ easy_image(src="mavlink-endpoints", width=600, class="pirate") }}
{% pirate() %}
- Endpoints intended for internal BlueOS operations are configured to the
loopback IP `127.0.0.1`
- Server endpoints for external use are configured to the localhost IP
   - e.g. `0.0.0.0`
   - `192.168.2.2` may also work
- Client endpoints for external use are configured to the external IP
   - e.g. `192.168.2.1` for connecting to a UDP server on the [Control Station Computer](@/hardware/required/control-computer/index.md)
- Client endpoints seem to operate more stably than server ones
- Unprotected endpoints can be removed or disabled
- Modifying an endpoint is not possible - a new one must be created instead
   - e.g. some users may wish to set up a UDP endpoint for connecting to with
   Pymavlink from the surface:
{% end %}
{{ easy_image(src="mavlink-endpoints-pymavlink-example", width=400, class="pirate") }}

{% pirate() %}
### NMEA Injector
{% end %}
{{ service(service="NMEA Injector", port=2748, link="/services/nmea_injector", based=true) }}
{% pirate() %}

- Conveys GPS positions (from an NMEA device) to the vehicle via MAVLink messages
{% end %}
{{ easy_image(src="nmea-injector", width=600, class="pirate") }}
{% pirate() %}
- Setup requires a UDP or TCP socket for the NMEA device to connect to, and a MAVLink ID
for the component that will send the location data to the vehicle
{% end %}
{{ easy_image(src="nmea-example", width=400, class="pirate") }}

### Ping Sonar Devices
{{ service(service="Ping Service", port=9110, link="/services/ping", based=true) }}

`New in 1.1`

The Ping Sonar Devices page shows any detected 
[sonars](@/hardware/additional/sonars/index.md) from the Ping family,
including [ethernet-configured Ping360s](https://bluerobotics.com/learn/changing-communications-interface-on-the-ping360/#wiring-connections--ethernet-configuration)
that are visible on the local network (e.g. via an 
[Ethernet Switch](@/hardware/additional/ethernet-switch/index.md)).

- Allows configuring Ping Sonar distance estimates to send as MAVLink
[`DISTANCE_SENSOR`](https://mavlink.io/en/messages/common.html#DISTANCE_SENSOR)
messages to the autopilot, for viewing in the Control Station Software and
logging as part of the telemetry stream
- Provides a viewing utility for devices connected via USB/serial, to show
which port they are plugged into 

{{ easy_image(src="ping-sonar-devices", width=600) }}

{% pirate() %}
### Serial Bridges
{% end %}
{{ service(service="Bridget", port=27353, link="/services/bridget", based=true) }}
{% pirate() %}

The Serial Bridges page allows creating high performance links between serial
devices that are connected to the onboard computer, to a UDP port. 

Replaces the [Routing](https://www.ardusub.com/reference/companion/routing.html)
functionality from the old Companion Software.

For making connections to the autopilot, see [MAVLink Endpoints](#mavlink-endpoints).
{% end %}
{{ easy_image(src="serial-bridges", width=600, class="pirate") }}
{% pirate() %}
- NOTE: UDP-based systems do not guarantee packet delivery or sequential alignment
- Bridges to the [Control Station Computer](@/hardware/required/control-computer/index.md)
  will generally use the localhost IP `0.0.0.0`, which creates a UDP server that waits
  for a UDP client on the control computer to connect to it
   - other IP addesses create a UDP client on the onboard computer, which expects the
     serial device to initiate communication before the connected UDP server (on the
     control computer) can respond
- Bridges to internal programs can use the loopback IP `127.0.0.1`, which creates a
  local server
{% end %}
{{ easy_image(src="serial-bridges-example", width=400, class="pirate") }}

### Vehicle Setup
`New in 1.1`

The Vehicle Setup page provides an overview of the vehicle, including its sensors and
peripherals.

{{ easy_image(src="vehicle-setup", width=600) }}

In future this page will allow 
- managing the output mappings
- testing the motors
- calibrating the autopilot sensors
- using custom 3D models and selection logic

### Video Streams
{{ service(service="MAVLink Camera Manager", link="https://github.com/bluerobotics/mavlink-camera-manager/", port=6020) }}

- BlueOS automatically detects H264-encoded video streams
{% pirate() %}
   - MJPG and YUYV encoded streams are also detected in pirate mode,
   but currently only work when configured as RTSP streams
{% end %}

- The first time BlueOS starts up it will auto-configure any cameras that are 
connected at that time, with UDP streams counting up from port `5600`
   - e.g. a second camera at first startup would be streamed to port `5601`
   - Auto-configuration also occurs if the settings are reset
      - applies to both [global settings resets](#settings) (via the sidebar) and
      - camera manager settings resets (via the settings icon in the bottom right)
- After the initial startup, settings are saved and persistent across reboots
   - Further changes require manually re-configuring streams
   - New streams need to be manually added
      - UDP stream endpoints should be set to `udp://<surface-IP>:<port>`
         - e.g. `udp://192.168.2.1:5602`
      - RTSP stream endpoints are auto-configured with appropriate values
   - One video input can have multiple output streams by clicking the blue `+`
   symbol during stream configuration
      - This only works for streams of the same endpoint type (e.g. it is not
      currently possible to mix UDP and RTSP output streams for the same input)

{{ simple_pirate_image(src="video-stream-example", width=400, center=true) }}

- The streams are also presented via MAVLink, so QGroundControl (>=v4.1.7) can
toggle between them without needing to know specific ports.
{% pirate() %}
   - It is possible to specify a stream as "thermal", which allows it to be
   overlaid on another stream in some viewing applications
{% end %}

{{ easy_image(src="qgc_switch_streams", width=400, center=true) }}

- Camera settings (brightness, exposure, etc) that are exposed via UVC can be
configured with the "Configure" button

{{ easy_image(src="video-config-example", width=500, center=true) }}

- Camera settings are also exposed via the
[MAVLink camera protocol](https://mavlink.io/en/services/camera.html), so are
controllable in QGroundControl
- Switching streams in QGroundControl while recording stops the current recording
   - If you are regularly switching streams it may be worth doing a screen recording
   either instead of or as well as recording the base video
- QGroundControl does not yet support displaying multiple streams simultaneously
   - Additional streams can be processed/viewed/recorded by [the options discussed
   here](https://discuss.bluerobotics.com/t/how-to-stream-another-cameras-video/9573/3#receiving-the-stream-7)
       - Note that some playback applications (e.g. VLC)  treat odd-numbered ports
       as audio channels, so relevant video streams should only use even-numbered
       ports
       - UDP streams have the option to download an SDP file (or copy a URL to it),
       for easier video playback in applications like VLC `(New in 1.1)`
- Raspberry Pi cameras are supported `(New in 1.1)`
   - Detection requires turning on legacy camera support:
      1. turn on via the settings button in the buttom right corner
      2. reboot the onboard computer to enable
{% pirate() %}
- It is possible to use the "Redirect source" element to make an ethernet camera
available via the BlueOS camera manager, which allows QGroundControl to detect
it automatically (via MAVLink)
{% end %}

{{ simple_pirate_image(src="video", width=600) }}

## Extensions

### Extensions Manager
`New in 1.1`
{{ service(service="Kraken", port=9134, link="/services/kraken", based=true) }}

The Extensions Manager is in charge of fetching, installing, updating, and managing
[Extensions](../extensions).

The Store tab shows
[the available extensions](https://docs.bluerobotics.com/BlueOS-Extensions-Repository/),
which can be clicked to see information about the extension (including the settings,
permissions requirements, and developer information), and allows selecting the version
to install:
{{ easy_image(src="extensions-store", width=600) }}
{{ easy_image(src="extensions-store-example", width=500) }}

The Installed tab shows the resource usage of the installed extensions, and allows
configuring them, checking their logs, and restarting or disabling them:
{{ simple_pirate_image(src="extensions-installed", width=600) }}

{% pirate() %}
Developers can install custom extensions as relevant.
{% end %}

{{ easy_image(src="extensions-installed-example", width=400, class="pirate") }}

## Interface Theme

### Theme Content
#### Vehicle Icon

- square images work best
- consider getting an image of your 3D model from the [Vehicle Setup](#vehicle-setup) page

{{ easy_image(src="theme-vehicle", width=500) }}

#### Vehicle Name and mDNS Hostname

- the vehicle name makes it easier to determine which vehicle you are connected to
- changing the mDNS hostname changes the address you connect to for the browser interface
    - ethernet tether -> [http://custom.local](http://custom.local)
    - wifi connection -> [http://custom-wifi.local](http://custom-wifi.local)
    - BlueOS hotspot -> [http://custom-hotspot.local](http://custom-hotspot.local)
    - [http://blueos.local](http://blueos.local) will still be available for direct ethernet
    connections, as a fallback in case the custom name is forgotten

{{ easy_image(src="theme-name-mdns", width=400) }}

#### Company Logo

- square images work best

{{ easy_image(src="theme-logo", width=500) }}

{% pirate() %}
### Theme Styling
It is possible to customise the styling of the BlueOS interface by adding a
`theme_style.css` file at `userdata/styles/` in the [File Browser](#file-browser).
The File Browser can also be used to modify the file, in which case the styles
are updated at the next page refresh after the file is saved. The save button is
in the top right corner.

[CSS](https://www.w3schools.com/html/html_css.asp) is commonly used for styling
HTML webpages, and has an extensive set of features available. For the purposes of
adjusting the BlueOS theme, the most important thing to understand is
[how to specify colors](https://www.w3schools.com/colors/default.asp). It can be
helpful to use tools like [colorhexa](https://www.colorhexa.com/5eabed) when
choosing a palette of colors, including for checking accessibility for various
color vision deficiencies.

For reference, here is an example with most of the main BlueOS colors changed,
together with the theme file that created it:

{% end %}

{{ easy_image(src="theme-style", width=600, class="pirate") }}

{% pirate() %}
```css
:root {
  --v-primary-base: #CAB1E5 !important;  /* sidebar highlights, submit buttons */
  --v-info-base: #BA55E5 !important;     /* info boxes (often same as primary base) */
  --v-warning-base: #EDD1E5 !important;  /* warnings and skip buttons */
  --v-error-base: #AC1D1C !important;    /* notifications, pirate icons, cancel/delete buttons */
  --v-anchor-base: #5A11ED !important;   /* hyperlinks */
}

/* light theme background, light to dark */
div.light-background {
  background-color: #BAFF1E !important;
  background-image: linear-gradient(160deg, #BAFF1E 0%, #5CA1E5 100%) !important;
}

/* dark theme background, light to dark */
div.dark-background {
  background-color: #5EABED !important;
  background-image: linear-gradient(160deg, #5EABED 0%, #BA55E5 100%) !important;
}

/* light theme header bar background, light to dark, translucent */
header.light-background-glass {
  background-color: #DEADBA55 !important; /* fallback if gradient not available */
  background-image: linear-gradient(160deg, #DEADBA88 0%, #5111CA88 100%) !important;
  backdrop-filter: blur(4.5px) !important;
  -webkit-backdrop-filter: blur(10px) !important;
}

/* dark theme header bar background, light to dark, translucent */
header.dark-background-glass {
  background-color: #5111CA55 !important; /* fallback if gradient not available */
  background-image: linear-gradient(160deg, #5111CA88 0%, #0B5E5588 100%) !important;
  backdrop-filter: blur(4.5px) !important;
  -webkit-backdrop-filter: blur(10px) !important;
}
```
{% end %}

<script type="text/javascript">
    function toggle_advanced() {
        if (document.querySelector('.pirate').style.display == 'none') {
            var show = '.pirate';
            var hide = '.simple';
            var buttonPrefix = "hide";
        } else {
            var show = '.simple';
            var hide = '.pirate';
            var buttonPrefix = "show";
        }
        [].forEach.call(document.querySelectorAll(show), function(el) {
            el.style.display = 'block';
        });
        [].forEach.call(document.querySelectorAll(hide), function(el) {
            el.style.display = 'none';
        });
        document.getElementById("pirate_toggle").textContent = 
            buttonPrefix+" advanced functionality";
    }
</script>
