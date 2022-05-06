+++
title = "Advanced Usage"
description = "BlueOS advanced usage documentation."
date = 2022-04-22T11:45:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
[extra]
lead = ''
toc = true
top = false
+++

## General Information

This documentation page is for detailed information about the services and pages
in the BlueOS web interface. For a higher level list and direct comparison of
features see the [Overview](../overview/#feature-comparison) instead.

### Pirate Mode

The default BlueOS interface is simplified, and shows only the major tools that
most people are likely to find useful. Full functionality is available via 
"Pirate Mode", which can be enabled from the [settings in the sidebar](#settings).

This documentation by default shows the full functionality interface, to provide
an overview of _all_ functionality instead of a limited subset, but if you're only
interested in the basic functionality you can click the button below:

<div style="text-align:center;padding-bottom:15px;">
<!-- functionality code at bottom of file -->
<button onclick="toggle_advanced()" id="pirate_toggle">
    hide advanced functionality
</button>
</div>

Any pages that are extended by (or only available in) Pirate Mode are shown in
[dark mode](#settings), and described with grey text.

### Main

When you first open BlueOS, you'll see a window like the following:
{{ simple_pirate_image(src="main", width=600) }}

#### Indicators and Network Configuration

On the right side of the header you'll find:
- Notifications
   - Press broom to clear notifications
   - Press cog to toggle showing old messages

{{ easy_image(src="notifications", width=350) }}

- Ethernet + static IP management - choose between:
   - A static IP
   - A DHCP server
   - A dynamic IP

{{ easy_image(src="ethernet", width=350) }}
{{ easy_image(src="ethernet-example", width=250) }}

- Wifi network management
   - Choose a network to connect to
   - Forget, connect to, or a force a new password for a saved network
{{ easy_image(src="wifi", width=350) }}
{{ easy_image(src="wifi-example", width=250) }}

- System status
   - Heartbeat icon pulses with vehicle heartbeat, and goes red if heartbeat is lost
   - On click shows onboard computer temperature, voltage, and current usage
   - Additional warning icons appear if onboard computer is too hot or under-powered
{{ easy_image(src="system-status", width=200) }}

#### Sidebar

The burger menu at the top left of the header opens up the side-bar, for
conveniently accessing available pages, tools, and services.

{{ simple_pirate_image(src="sidebar", width=200) }}

##### Settings

{{ simple_pirate_image(src="settings", width=300) }}

- Reset BlueOS settings
   - Remove existing camera/endpoint/bridges configuration
- Pirate mode toggle
   - Access or hide advanced functionality
- Dark mode toggle
   - Change between light and dark viewing modes

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
- Restart core container
   - Restart the core BlueOS docker container
   - Generally sufficient for most 'reboot' requirements
{% end %}

##### Feedback

{{ easy_image(src="feedback", width=300) }}

Submit feedback about BlueOS via:
- Issues on the GitHub repository (allows easily tracking changes, 
and notification when complete/fixed)
- Posts on the Blue Robotics forum (allows easy discussion with the community)
- Messages in the Blue Robotics Slack (for internal use)

## Vehicle

### General
The "General" page provides basic info about the active autopilot, along with
options to:
- Change board (select a connected board, or run an 
[SITL](https://www.ardusub.com/developers/sitl.html) simulation)
- Restart the autopilot
{% pirate() %}
- Start the autopilot
- Stop the autopilot
{% end %}

{{ simple_pirate_image(src="general", width=600) }}

### Firmware
- [ArduPilot](ardupilot.org) family of firmwares only
- Choose firmware to install
   - Select from the online repository
      - Select vehicle type (Sub / Rover / Plane / Copter)
      - Select desired release and stability level
         - Official - The latest stable release. Recommended for most users.
         - Stable - A production-ready release. Suitable for most users.
         - Beta - In-testing release, with new features and improvements, aiming
         to become stable. May have bugs.
         - Dev - Development branch, with all the newest features. Intentionally
         unstable (changes quickly), and possible untested/dangerous.
   - Upload a custom firmware file from the surface computer
   - Restore the default (ArduSub) firmware for the connected flight controller
- Flash firmware onto a connected compatible flight controller board

{{ easy_image(src="firmware", width=600) }}

### Log Browser
- Built in version of 
[UAV LogViewer](https://ardupilot.org/copter/docs/common-uavlogviewer.html)
for powerful analysis of vehicle telemetry
- Currently only set up to fetch logs automatically from Linux-based autopilots
   - e.g. Pixhawk **not** yet supported

{{ easy_image(src="log-browser", width=600) }}

### Video
- BlueOS automatically detects H264-encoded video streams
- The first time BlueOS starts up it will auto-configure any cameras that are 
connected at that time, with UDP streams counting up from port 5600
   - e.g. a second camera at first startup would be streamed to port 5601
   - Auto-configuration also occurs if the [settings are reset](#settings)
{% pirate() %}
      - It's also possible to manually reset _only_ the camera settings by deleting
      the file `/root/.config/mavlink-camera-manager/settings.json` via
      [the file browser](#file-browser) or [the terminal](#terminal)
{% end %}

- After the initial startup, settings are saved and persistent across reboots
   - Further changes require manually re-configuring streams
   - New streams need to be manually added
      - The stream endpoint should be set to `udp://<surface-IP>:<port>`
      - e.g. `udp://192.168.2.1:5601`
- The streams are also presented via MAVLink, so QGroundControl (v4.1.7) can
toggle between them without needing to know specific ports.
<div style="text-align:center;">

{{ easy_image(src="qgc_switch_streams", width=400) }}

</div>

- Camera settings (brightness, exposure, etc) that are exposed via UVC can be
configured with the "Configure" button
- Switching streams in QGroundControl while recording stops the current recording
   - If you are regularly switching streams it may be worth doing a screen recording
   either instead of or as well as recording the base video
- QGroundControl does not yet support displaying multiple streams simultaneously
   - Additional streams can be processed/viewed/recorded by [the options discussed
   here](https://discuss.bluerobotics.com/t/how-to-stream-another-cameras-video/9573/3#receiving-the-stream-7)
- Raspberry Pi cameras are **not yet supported** in the pre-built releases/images
   - It is possible to do a custom installation on Raspberry Pi OS Buster or
   manually enable the legacy camera stack on Bullseye if necessary

{{ simple_pirate_image(src="video", width=600) }}

{% pirate() %}
### Endpoints
The endpoint manager allows managing the serial and UDP MAVLink endpoints and
routing configurations.
{% end %}
{{ easy_image(src="endpoints", width=600, class="pirate") }}
{% pirate() %}
- Endpoints intended for internal BlueOS operations are configured to the
loopback IP `127.0.0.1`
- Server endpoints for external use are configured to the localhost IP (e.g.
`0.0.0.0`; `192.168.2.2` may also work)
- Client endpoints for external use are configured to the external IP (e.g.
`192.168.2.1`)
- Client endpoints seem to operate more stably than server ones
- Unprotected endpoints can be removed or disabled:
{% end %}
{{ easy_image(src="endpoints-disable-delete", width=400, class="pirate") }}
{% pirate() %}
- Modifying an endpoint is not possible - a new one must be created instead
   - e.g. some users may wish to set up a UDP endpoint for connecting to with
   Pymavlink from the surface:
{% end %}
{{ easy_image(src="endpoints-pymavlink-example", width=400, alt_extra="Example", class="pirate") }}

## Tools

### System Information
The system information page provides useful information about the processes,
network configuration, and computer system BlueOS is running on. It can be
useful for troubleshooting, and finding if a particular program is using
excessive resources.
{{ easy_image(src="system-info-processes", width=600) }}
{{ easy_image(src="system-info-monitor", width=600) }}
{{ easy_image(src="system-info-network", width=600) }}
{{ easy_image(src="system-info-about", width=600) }}

### Network Test
The Network Test page measures real-time latency between BlueOS and the surface
computer, and allows checking the upload and download speeds between them.

{{ easy_image(src="network-test", width=600) }}

### Version Chooser
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
- If necessary, the underlying service can be accessed directly at TCP port `8081`
   - e.g. http://blueos.local:8081
{% end %}

{% pirate() %}
### Available Services

The Available Services page provides developer access to the underlying http
server interfaces of the services upon which BlueOS is based. Each service is
listed with 
- the port it is served at
- a meaningful name
- a web-page link using the active 
[network configuration](../getting-started/#interface-access), and where relevant
- its API documentation (in a live-testable form)
- the current API version
{% end %}
{{ easy_image(src="available-services", width=600, class="pirate") }}

{% pirate() %}
### Bridges

The Bridges page allows creating high performance links between serial devices
that are connected to the onboard computer, to a UDP port.
{% end %}
{{ easy_image(src="bridges", width=600, class="pirate") }}
{% pirate() %}
- NOTE: UDP-based systems do not guarantee packet delivery or sequential alignment
- Bridges to external devices will generally use the localhost IP `0.0.0.0`
- Bridges to internal programs can use the loopback IP `127.0.0.1`
{% end %}
{{ easy_image(src="bridges-example", width=400, class="pirate") }}

{% pirate() %}
### File Browser
The File Browser allows viewing, editing, downloading, and uploading BlueOS files
{% end %}
{{ easy_image(src="file-browser", width=600, class="pirate") }}
{% pirate() %}
> **NOTE:** There is 
> [a known issue](https://github.com/bluerobotics/BlueOS-docker/issues/1004)
> where the File Browser does not load properly with certain browsers. It is
> fixed in the 1.1.x beta releases, but in the interim for current stable
> releases it's possible to access the underlying service at 
> http://blueos.local:7777
{% end %}

{% pirate() %}
### NMEA Injector
- Conveys GPS positions (from an NMEA device) to the vehicle via MAVLink messages
{% end %}
{{ easy_image(src="nmea-injector", width=600, class="pirate") }}
{% pirate() %}
- Setup requires a socket for the NMEA device to connect to, and a MAVLink ID for
the component that will send the location data to the vehicle
{% end %}
{{ easy_image(src="nmea-example", width=400, class="pirate") }}

{% pirate() %}
### Terminal
The terminal provides
- A tmux session
- Direct access into the core BlueOS docker container
- Ready access to the tmux sessions of the core services (`CTRL+b s`)
   - Useful for seeing logs as they update live
   - Can kill services if necessary
- Access to the underlying device via the `red-pill` utility
{% end %}
{{ easy_image(src="terminal", width=600, class="pirate") }}

{% pirate() %}
### MAVLink Inspector
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
