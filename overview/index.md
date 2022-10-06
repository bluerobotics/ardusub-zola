+++
title = "Overview"
description = "BlueOS overview."
date = 2022-04-28T21:25:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
[extra]
lead = 'BlueOS is a modular, robust, and efficient platform for managing a vehicle or robot from its onboard computer.'
toc = true
top = false
+++

## A bit of context...

The [original Companion](https://www.ardusub.com/reference/companion-web-ui.html) project (started in 2015) was originally created with the simple intent to route an underwater vehicle's video stream and communications to the surface computer, and provide some basic configuration of those features and the vehicle firmware. The simple scope was great to get things started, but also meant that new and complex features weren't designed in from the start, so maintenance and developing functionality have been increasingly challenging.

With lessons learned on useful features and software architecture requirements, BlueOS was designed and created from the ground up to fit the requirements of the onboard computer system we _want_ to have - with room to grow into a true operating system for the vehicle. BlueOS is modular to the heart, which makes it portable, robust to update, and extensible. 

There are many upcoming features, including support for [third party packages](https://discuss.bluerobotics.com/t/external-integrations-extensions/10912), applications, advanced data logging, and much more! We're super excited about our future with BlueOS, and we can't wait for you to join us and try it out! 😄

## BlueOS principles and goals

As the core development team we've tried to envision the future of the onboard computer, and the features that will require. Our initial ideas have been distilled into the following core concepts, many of which are already built in to the BlueOS of today:

* An interface that is **simple by default but powerful when needed** - the user has the power to change anything they desire and customize the full experience
* **Designed to focus on what matters**, improving user access to information and controls with a human-friendly UI and UX
* **Make complex tasks simpler** and improve ease of use by reusing design patterns from other applications (based on the [material UI guidelines](https://material.io/design/guidelines-overview))
* **Advanced error handling and detection**, making any problems clear to the user and developers, along with how to fix them
* **Simplify development**, providing full access to our services API and modular development model
* **Encourage contributions**, [the project is open source](https://github.com/bluerobotics/BlueOS-docker)!
* **Portable and flexible**, you should be able to run on a Raspberry Pi 3/4 or any SBC with Linux operating system, contributions are welcomed
* **Highly functional with low CPU usage**, the entire system is built to run efficiently
* **Developed on solid foundations**, critical parts or intensive workforce services are designed using the most advanced languages and features available for stability

Some of these principles will only be evident in future releases, but the underlying software architecture and organization have been designed from the ground up to support and enable them.


## Feature Comparison

BlueOS has most of the features from the old Companion, and some hotly-requested new ones too!

| Feature | Companion | BlueOS | Both |
|---|---|---|---|
| **Hardware** | Raspberry Pi 3B required | Raspberry Pi 3B / 3B+ / 4B supported;<br>Other Linux-based SBCs images to come;<br>You can install from scratch using the installation script in any Linux computer. (Modifications may be necessary for your hardware configuration) |  |
| [**WIFI manager**](../advanced-usage/#indicators-and-network-configuration) | Connect to a *single network* | Connect to and manage *multiple networks*, like a cellphone or computer WIFI manager | Visible and hidden networks supported |
| [**Ethernet manager**](../advanced-usage/#indicators-and-network-configuration) | *Single* DHCP *or* static network | *Multiple* static IPs *and* DHCP configuration | DHCP client or server |
| [**Camera manager**](../advanced-usage/#video) | Select a *single* camera to stream over UDP<br>Supports Raspberry Pi cameras ([except HQ Camera](https://discuss.bluerobotics.com/t/raspberry-pi-camera-stream-not-working/11976/18))<br>Supports a single audio stream over UDP | Easily manage *multiple streams*<br><br>UDP, RTSP and support coming soon for WebRTC ([#1000](https://github.com/bluerobotics/BlueOS-docker/issues/1000))<br><br>Raspberry Pi cameras<br>*not yet supported* ([#991](https://github.com/bluerobotics/BlueOS-docker/issues/991))<br><br>Audio streaming<br>*not yet supported* ([#990](https://github.com/bluerobotics/BlueOS-docker/issues/990)) | H264-encoded streams only |
| [**NMEA support**](../advanced-usage/#nmea-injector) | - | - | Conveys GPS positions to the vehicle |
| **Ping Sonar Devices** | Ping Sonar distance estimates can be *sent via MAVLink* | Devices can be *hot-plugged*<br><br>MAVLink pipeline<br>*not yet supported* ([#264](https://github.com/bluerobotics/BlueOS-docker/issues/264)) | Ping Sonar and Ping360 can connect with [Ping Viewer](https://docs.bluerobotics.com/ping-viewer/) |
| [**ArduPilot Firmware**](../advanced-usage/#firmware) | *ArduSub-only* downloads | *General ArduPilot* downloads;<br>*select vehicle* to update | `stable`, `beta`, and `devel` releases, custom uploads, and restore default parameters |
| [**Endpoints**](../advanced-usage/#endpoints) | - | - | Create and manage UDP, TCP, and serial MAVLink endpoints |
| [**Bridges**](../advanced-usage/#bridges) | - | - | Create and manage bridges between serial and UDP endpoints |
| [**File Browser**](../advanced-usage/#file-browser) | - | *Edit files* from the browser | Download and upload files |
| [**Log manager**](../advanced-usage/#log-browser) | Ssh/terminal only | *Download and manage logs* from the browser |  |
| [**Log Viewer**](../advanced-usage/#log-browser) | - | *Visualise and analyse logs* from the browser |  |
| [**Web Terminal**](../advanced-usage/#terminal) | Access Linux terminal from the browser | Access Linux terminal with a tmux session from the browser | Web terminal client |
| [**Version Chooser**](../advanced-usage/#version-chooser) | Update to *latest stable only* | *Easily update/downgrade* between versions, including locally stored;<br>Includes *stable, beta, and master* releases*;<br>Available even if main site failing |  |
| [**System information**](../advanced-usage/#system-information) | Basic usage statistics, list of connected devices | Provides all the necessary information about the hardware, operating system, running processes, CPU, memory, disk, network usage and status |  |
| [**Notification system**](../advanced-usage/#indicators-and-network-configuration) | - | Notifications about issues, new releases, and the status of your system. |  |
| [**Network test**](../advanced-usage/#network-test) | - | Check *real time latency* | Check upload and download speed from the surface computer to the vehicle |
| [**MAVLink inspector**](../advanced-usage/#mavlink-inspector) | See latest MAVLink messages via MAVLink2REST | see and *inspect MAVLink messages in real time* from the browser | MAVLink2REST is available |
| **Water Linked** | Supports UGPS and DVL-A50 | [DVL-A50 package available](https://discuss.bluerobotics.com/t/external-integrations-extensions/10912#integration-example-dvl-5);<br>UGPS *not yet supported* |  |

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

It's worth noting that [Version Chooser](../advanced-usage/#version-chooser) in general offers several major robustness and versatility improvements over the previous 'latest update only' approach, which should benefit both users and developers.

## Quick links

1. [Documentation](../)
2. [Source code](https://github.com/bluerobotics/BlueOS-docker)
3. [Releases, changelogs, files](https://github.com/bluerobotics/BlueOS-docker/releases)
