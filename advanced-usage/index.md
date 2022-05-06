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

### Pirate Mode

<!-- functionality code at bottom of file -->
<button onclick="toggle_advanced()" id="pirate_toggle">
    hide advanced functionality
</button>

### Main

When you first open BlueOS, you'll see a window like the following:
{{ simple_pirate_image(src="main", width=600) }}

#### Indicators and Network Configuration

On the right side of the header you'll find:
- notifications
   - press broom to clear notifications
   - press cog to toggle showing old messages

{{ easy_image(src="notifications", width=350) }}


- ethernet + static IP management - choose between:
   - a static IP
   - a DHCP server
   - a dynamic IP

{{ easy_image(src="ethernet", width=350) }}
{{ easy_image(src="ethernet-example", width=250) }}

- wifi network management
   - choose a network to connect to
   - forget, connect to, or a force a new password for a saved network
{{ easy_image(src="wifi", width=350) }}
{{ easy_image(src="wifi-example", width=250) }}

- system status
   - heartbeat icon pulses with vehicle heartbeat, and goes red if heartbeat is lost
   - on click shows onboard computer temperature, voltage, and current usage
   - additional warning icons appear if onboard computer is too hot or under-powered
{{ easy_image(src="system-status", width=200) }}

#### Sidebar

{{ simple_pirate_image(src="sidebar", width=200) }}

##### Settings

{{ simple_pirate_image(src="settings", width=300) }}

- reset BlueOS settings
   - remove existing camera/endpoint/bridges configuration
- pirate mode toggle
   - access or hide advanced functionality
- dark mode toggle
   - change between light and dark viewing modes

##### Power

{{ simple_pirate_image(src="power", width=300) }}

- power off
   - shut down onboard computer
   - recommended before turning off vehicle power
- reboot
   - reboot onboard computer
{% simple() %}
- soft restart
   - do a software-restart of BlueOS (without restarting the computer)
   - generally sufficient for most 'reboot' requirements
{% end %}
{% pirate() %}
- restart core container
   - restart the core BlueOS docker container
   - generally sufficient for most 'reboot' requirements
{% end %}

##### Feedback

{{ easy_image(src="feedback", width=400) }}

Submit feedback about BlueOS via:
- Issue on the GitHub repository (allows easily tracking changes, 
and notification when complete/fixed)
- Post on the Blue Robotics forum (allows easy discussion with the community)
- Message in Blue Robotics Slack (internal company use only)

## Vehicle

### General
- Basic info about active Autopilot
- Change Board (select connected board, or SITL simulation)
- Restart Autopilot
{% pirate() %}
- Start Autopilot
- Stop Autopilot
{% end %}

{{ simple_pirate_image(src="general", width=600) }}

### Firmware (ArduPilot)
- Select vehicle type
- Select release (master, beta, stable)
- Flash
{% pirate() %}
- underlying service page (url)
{% end %}

{{ easy_image(src="firmware", width=600) }}

### Log Browser
- Navigator only for now (#...)

{{ easy_image(src="log-browser", width=600) }}

### Video
- auto-detect H264 cameras
- when first connected it connects to and streams all cameras and counts
ports from 5600
- after that settings are saved, so need to reset settings for auto-streaming
- can manually set up camera streams
- RPi cameras not yet supported

{{ simple_pirate_image(src="video", width=600) }}

{% pirate() %}
### Endpoints
- Clients seem to be most stable

{% end %}
{{ easy_image(src="endpoints", width=600, class="pirate") }}
{{ easy_image(src="pymavlink-endpoint", width=400, alt_extra="Example", class="pirate") }}

## Tools

### System Information

{{ easy_image(src="system-info-processes", width=600) }}
{{ easy_image(src="system-info-monitor", width=600) }}
{{ easy_image(src="system-info-network", width=600) }}
{{ easy_image(src="system-info-about", width=600) }}

### Network Test

{{ easy_image(src="network-test", width=600) }}

### Version Chooser
- update to latest version of similar or increased stability
{% pirate() %}
- switch between versions
- load remote versions (including from custom (docker-hub?) repositories)
- manually upload docker image
{% end %}

{{ simple_pirate_image(src="version-chooser", width=600) }}

{% pirate() %}
### Available Services

{% end %}
{{ easy_image(src="available-services", width=600, class="pirate") }}

{% pirate() %}
### Bridges

{% end %}
{{ easy_image(src="bridges", width=600, class="pirate") }}
{{ easy_image(src="bridges-example", width=400, class="pirate") }}

{% pirate() %}
### File Browser

{% end %}
{{ easy_image(src="file-browser", width=600, class="pirate") }}

{% pirate() %}
### NMEA Injector

{% end %}
{{ easy_image(src="nmea-injector", width=600, class="pirate") }}
{{ easy_image(src="nmea-example", width=400, class="pirate") }}

{% pirate() %}
### Terminal

{% end %}
{{ easy_image(src="terminal", width=600, class="pirate") }}

{% pirate() %}
### MAVLink Inspector

{% end %}
{{ easy_image(src="mavlink-inspector", width=600, class="pirate") }}

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
            el.style.display = 'contents';
        });
        [].forEach.call(document.querySelectorAll(hide), function(el) {
            el.style.display = 'none';
        });
        document.getElementById("pirate_toggle").textContent = 
            buttonPrefix+" advanced functionality";
    }
</script>
