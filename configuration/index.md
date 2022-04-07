+++
title = "Configuration / Usage"
description = "BlueOS Docker configuration instructions."
date = 2021-10-20T22:20:00+00:00
template = "docs/page.html"
sort_by = "weight"
weight = 20
draft = false
[extra]
lead = ''
toc = true
top = false
+++
## Network Configuration

Your topside computer’s network configuration should be the same as for the previous Companion software.
To configure it, you can follow our [network setup instructions](https://www.ardusub.com/quick-start/installing-companion.html#network-setup).

## New Web Interface

BlueOS is designed to be a modular collection of services, which generally each provide a REST API, documentation, and a development webpage.
The web interface monitors the autopilot and other main software components, and also listens for and displays connections from other HTTP servers (on TCP ports) and docker containers, so you can keep your own integrations isolated from the normal BlueOS release/update cycle.

### Interface Access

You can access BlueOS via the old IP address ([192.168.2.2](http://192.168.2.2/)) or via [blueos.local](http://blueos.local/), to connect with it via wifi, it's possible to use [blueos-wifi.local](http://blueos-wifi.local/).

### Interface Features

When you first open the web interface, you'll see a page that looks like this:
<img src="main-page.png" width="650">

Of particular note is the header, which contains:
- the main hamburger menu (top left corner), for managing your flight controller and accessing some useful tools, and
- health, wifi, network, and notification indicators (top right corner)

## Updating / Releases

There are 3 types of releases for BlueOS:
1. Stable releases
   - Stable versions with long-term support
2. B.E.T.A. releases
   - Versions that will be released after an internal test
3. Master releases (highly volatile, not recommended)
   - The very latest features, that may not have been tested yet

We recommend using only the stable releases.

Versions and change-logs are on the [GitHub versions page](https://github.com/bluerobotics/blueos-docker/releases)

### Connect Wifi

When starting out, it's important to connect to wifi so you can update to the latest suitable release.

1. First, click the wifi indicator to scan for available wifi networks

   ![Wifi Scan](wifi-scan.png)
1. Select the desired network, type in the password, and click connect

   ![Wifi Login](wifi-login.png)
1. Once connected, the wifi icon will change to show the signal strength, and the connected wifi network will be selected on the menu

   ![Wifi Confirm](wifi-confirm.png)

### Select Version

Now that your BlueOS has an internet connection, you can perform the update to the latest available version.

1. Click on the hamburger menu

   ![Version Menu](version-menu.png)
1. Under **tools**, select **Version-Chooser**

   ![Version Chooser](version-chooser.png)
1. If you're already on the latest version, the right side of your Local Version will be blank. If not, you should see a blue **Update** button.

   <img src="version-update.png" width="650">
2. It's also possible to update between different versions (When pirate mode is enabled)

   <img src="version-options.png" width="650">
3. Once the update button is clicked the update process will run.
   Please wait until it finishes - it will automatically reload the webpage for you.

## Camera Streams

> **Note:** A connected H264 camera should be automatically configured as a default stream by the camera manager when you start BlueOS. If not, make sure your camera is properly connected, and that BlueOS is on the latest available version. Reset settings and restart BlueOS if necessary.

The BlueOS software is capable of configuring and streaming multiple cameras simultaneously. Only one will be set up as the default stream, so if it's not the one you wanted (or if you want several streams) then these instructions cover how to set up a stream manually.

1. Go to Autopilot / Video in the hamburger menu of the web interface

   ![Video Menu](video-menu.png)
1. Click "Add Stream" on the desired camera

   ![Video Select](video-select.png)
1. Specify a name, select the stream properties, and click "Create"

   ![Video Stream](video-stream.png)
