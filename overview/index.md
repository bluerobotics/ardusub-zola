+++
title = "Overview"
description = "BlueOS overview."
date = 2024-04-10T11:45:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
aliases = ['/software/onboard/BlueOS-latest/overview', '/blueos/latest/overview']

[extra]
lead = 'BlueOS is a modular, robust, and efficient platform for managing a vehicle or robot from its onboard computer.'
toc = true
top = false
+++

## A bit of context...

The [original Companion Software](https://www.ardusub.com/reference/companion-web-ui.html) project (started in 2015) was originally created with the simple intent to route an underwater vehicle's video stream and communications to the surface computer, and provide some basic configuration of those features and the vehicle firmware. The simple scope was great to get things started, but also meant that new and complex features weren't designed in from the start, so maintenance and developing functionality became increasingly challenging.

With lessons learned on useful features and software architecture requirements, BlueOS was designed and created from the ground up to fit the requirements of the onboard computer system we _want_ to have - with room to grow into a true operating system for the vehicle. BlueOS is modular to the heart, which makes it portable, robust to update, and extensible. 

We're super excited about our future with BlueOS, and we can't wait for you to join us and try it out! 😄

## BlueOS principles and goals

As the core development team we've tried to envision the future of the onboard computer, and the features that will require. Our initial ideas have been distilled into the following core concepts, many of which are already built in to the BlueOS of today:

* An interface that is **simple by default but powerful when needed** - the user has the power to change anything they desire and customize the full experience
* **Designed to focus on what matters**, improving user access to information and controls with a human-friendly UI and UX
* **Make complex tasks simpler** and improve ease of use by reusing design patterns from other applications (based on the [material UI guidelines](https://material.io/design/guidelines-overview))
* **Advanced error handling and detection**, making any problems clear to the user and developers, along with how to fix them
* **Simplify development**, providing full access to our services API and modular development model
* **Encourage contributions**, [the project is open source](https://github.com/bluerobotics/BlueOS)!
* **Portable and flexible**, you should be able to run on a Raspberry Pi 3/4 or any SBC with Linux operating system, contributions are welcomed
* **Highly functional with low CPU usage**, the entire system is built to run efficiently
* **Developed on solid foundations**, critical parts or intensive workforce services are designed using the most advanced languages and features available for stability

Some of these principles will only be evident in future releases, but the underlying software architecture and organization have been designed from the ground up to support and enable them.

## What's New in BlueOS-1.2?

This covers a summary of the major changes and new features in BlueOS-1.2. Where applicable relevant features are also included in the [feature comparison table](#feature-comparison). For detailed coverage of every change, please see the [full release notes](https://github.com/bluerobotics/BlueOS-docker/releases).

### [Bootstrap](../development/bootstrap/)
- Resolves the issue where BlueOS would revert to its factor image
   - It is recommended to update bootstrap via the [BlueOS Version](../advanced-usage/#blueos-version)
     once you have updated to BlueOS 1.2 (requires turning on [Pirate Mode](../advanced-usage/#pirate-mode))

### [Extensions](../development/extensions/)
- A standard folder for binding to the filesystem, accessible from the [File Browser](../advanced-usage/#file-browser)
- Support for custom SVG icons
- Development process documentation
- [BlueOS-Community GitHub organisation](https://github.com/orgs/BlueOS-community/repositories), including
   - Open-source extension examples
   - A [deployment action](https://github.com/BlueOS-community/Deploy-BlueOS-Extension), for automatic building and upload of extension Docker images
   - Extension development quickstart/template repositories

### Page improvements
- [Vehicle Setup](../advanced-usage/#vehicle-setup)
   - Improved sensor status indicators
   - COMING SOON: sensor calibrations, improved peripheral configuration
- [Extensions Manager](../advanced-usage/#extensions-manager)
   - Added disk usage display for installed extensions
- [MAVLink Endpoints](../advanced-usage/#mavlink-endpoints)
   - Added MAVP2P as an alternative MAVLink routing option
- [File Browser](../advanced-usage/#file-browser)
   - New shortcuts to useful parts of the file-system

### Device/Hardware Support
- Improved development support for devices without a default `pi` user, and that should have some services disabled on startup

## Feature Comparison

BlueOS has almost all features from the old Companion, and several hotly-requested new ones too!

| Feature | BlueOS 1.2 | BlueOS 1.1 | BlueOS 1.0 | Companion |
|---|---|---|---|---|
| [**Onboard Computer**](@/hardware/required/onboard-computer/index.md) | &rarr; | &rarr;<br>+ Other Linux-based SBCs images to come | + Raspberry Pi 3B / 3B+ / 4B supported<br>+ You can install from scratch using the installation script in any Linux computer. (Modifications may be necessary for your hardware configuration) | Raspberry Pi 3B required |
| [**Flight Controller**](@/hardware/required/flight-controller/index.md) | &rarr; | &rarr;<br>+ Cube Orange<br>+ Pixhawk 6X | &rarr;<br>+ Navigator<br>+ Pixhawk 4 | Pixhawk |
| [**Video Streams**](../advanced-usage/#video-streams) | &rarr; | &rarr;<br>+ MPEG and YUYV encodings<br><br>+ Supports Raspberry Pi cameras | + Easily manage *multiple streams*<br><br>+ UDP and RTSP outputs<br><br>- Audio streaming<br>*not yet supported* ([#990](https://github.com/bluerobotics/BlueOS-docker/issues/990)) | Select a *single* camera to stream over UDP<br>+ Supports Raspberry Pi cameras ([except HQ Camera](https://discuss.bluerobotics.com/t/raspberry-pi-camera-stream-not-working/11976/18))<br>+ Supports a single audio stream over UDP |
| [**WIFI Manager**](../advanced-usage/#indicators-and-network-configuration) | &rarr; | &rarr;<br>+ Vehicle provides local hotspot | &rarr;<br>+ Connect to and manage *multiple networks*, like a cellphone or computer WIFI manager | Connect to a *single network*<br>+ Visible and hidden networks supported |
| [**Ethernet Manager**](../advanced-usage/#indicators-and-network-configuration) | &rarr; | &rarr; | *Multiple* static IPs *and* DHCP configuration | *Single* DHCP (client or server) *or* static network |
| [**Notification system**](../advanced-usage/#header-indicators-and-blueos-configuration) | &rarr; | &rarr; | Notifications about issues, new releases, and the status of your system. | - |
| [**File Browser**](../advanced-usage/#file-browser) | &rarr;<br>+ Folder for extension data and configuration files | &rarr; | &rarr;<br>+ *Edit files* from the browser | Download and upload files |
| [**Log Browser**](../advanced-usage/#log-browser) | &rarr; | &rarr; | *Download and manage logs* from the browser<br>+ *Visualise and analyse logs* from the built in viewer | Ssh/terminal only |
| [**MAVLink inspector**](../advanced-usage/#mavlink-inspector) | &rarr; | &rarr;<br>+ MAVLink2REST "watcher" option for individual message types | See and *inspect MAVLink messages in real time* from the browser | See latest MAVLink messages via MAVLink2REST |
| [**Network test**](../advanced-usage/#network-test) | &rarr; | &rarr;<br>+ Graph during speed tests | &rarr;<br>+ Check *real time latency* | Check upload and download speed from the Control Station Computer to the vehicle's Onboard Computer |
| [**System information**](../advanced-usage/#system-information) | &rarr; | &rarr; | Provides all the necessary information about the hardware, operating system, running processes, CPU, memory, disk, network usage and status | Basic usage statistics, list of connected devices |
| [**Web Terminal**](../advanced-usage/#terminal) | &rarr;<br>+ Support for non-`pi` users | &rarr; | &rarr;<br>+ Uses a tmux session | Access Linux terminal from the browser |
| [**Autopilot Firmware**](../advanced-usage/#autopilot-firmware) | &rarr; | &rarr; | &rarr;<br>+ *General ArduPilot* downloads;<br>+ *select vehicle* to update | `stable`, `beta`, and `devel` releases, custom uploads, and restore default parameters;<br>*ArduSub-only* downloads |
| [**Autopilot Parameters**](../advanced-usage/#autopilot-parameters) | &rarr; | View, search, and edit vehicle parameters | - | - |
| [**Version Chooser**](../advanced-usage/#blueos-version) | &rarr; | &rarr;<br>+ Bootstrap updates | + *Easily update/downgrade* between BlueOS versions, including locally stored<br>+ Includes *stable, beta, and master* releases*<br>+ Available even if main site failing | Update Companion to *latest stable only* |
| [**MAVLink Endpoints**](../advanced-usage/#mavlink-endpoints) | &rarr; | &rarr; | &rarr; | Create and manage UDP, TCP, and serial MAVLink endpoints |
| [**NMEA support**](../advanced-usage/#nmea-injector) | &rarr; | &rarr; | &rarr; | Conveys GPS positions to the vehicle |
| [**Ping Sonar Devices**](../advanced-usage/#ping-sonar-devices) | &rarr; | &rarr;<br>+ Detects Ping360 in ethernet configuration<br>+ Ping Sonar distance estimates can be *sent via MAVLink* | &rarr;<br>+ Devices can be *hot-plugged*<br><br>- *No MAVLink pipeline* | Ping Sonar and Ping360 can connect with [Ping Viewer](https://docs.bluerobotics.com/ping-viewer/)<br>+ Ping Sonar distance estimates can be *sent via MAVLink* |
| [**Serial Bridges**](../advanced-usage/#serial-bridges) | &rarr; | &rarr; | &rarr; | Create and manage bridges between serial and UDP/TCP endpoints |
| **Water Linked** | &rarr; | DVL-A50 and UGPS extensions available through Extensions Manager | [DVL-A50 package available](https://discuss.bluerobotics.com/t/external-integrations-extensions/10912#integration-example-dvl-5) | Supports UGPS and DVL-A50 |
| [**Extensions**](../extensions/) | &rarr; | Custom extensions available through Extensions Manager | &rarr; | Custom functionality requires forking the codebase |

## Release Types
BlueOS has multiple release types, to allow choosing your preferred balance between access to the latest fixes and improvements, and stability of the software. The three release types are:
- **Stable:** Officially tested and validated
   - Stable versions with long term support
   - Recommended for most users
- **Beta:** Quick-passed rolling releases with new features, bug fixes and general improvements
   - Versions that will be released after an internal test
   - A taste of what's to come
- **Master:** Rapidly-passed *bleeding edge* development releases 🔥
   - The very latest features, that may not have been tested yet
   - Highly volatile, generally not recommended
   - For those who want to live in the future

When BlueOS is connected to the internet, a notification appears if a newer version of the same release or a *stabler* type is available. E.g: When using a **Stable** version, _**only**_ new **Stable** versions will trigger a notification. If using a **Beta** release, newer **Beta** and **Stable** releases will trigger a notification. When running **Master**, any release type newer than the active one will trigger a new update notification. This helps to ensure that any updates will be as or more stable than your current version, unless you intentionally change to a less stable release type.

It's worth noting that the [Version Chooser](../advanced-usage/#blueos-version) in general offers several major robustness and versatility improvements over the previous 'latest update only' approach, which should benefit both users and developers.

## Quick links

1. [Documentation](../)
2. [Source code](https://github.com/bluerobotics/BlueOS)
3. [Releases, changelogs, files](https://github.com/bluerobotics/BlueOS/releases)
