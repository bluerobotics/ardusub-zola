+++
title = "Getting Started"
description = "BlueOS getting started instructions."
date = 2023-02-23T23:15:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 20
draft = false
aliases = ['/software/onboard/BlueOS-latest/getting-started']

[extra]
lead = ''
toc = true
top = false
+++
## Network Configuration

Your topside computer’s network configuration should be the same as for the previous Companion software.
To configure it, you can follow our [network setup instructions](https://www.ardusub.com/quick-start/installing-companion.html#network-setup).

## Web Interface

BlueOS is designed as a modular collection of services, which are accessed and configured via a combined web interface.

The web interface monitors the autopilot and other main software components. It also listens for and displays connections from other HTTP servers (on TCP ports), which allows extensions and custom integrations to provide an interface through BlueOS while remaining independent from the main BlueOS release/update cycle.

### Interface Access

By default you can access BlueOS via the old IP address ([192.168.2.2](http://192.168.2.2/)) or via [blueos.local](http://blueos.local/).
When BlueOS is connected to the same wifi network as your device you can also connect with it using [blueos-wifi.local](http://blueos-wifi.local/).

### Interface Features

When you first open the web interface, you'll see a page that looks like this:
{{ easy_image(src="../advanced-usage/interface-overview", width="600") }}

As a brief overview,
- the header contains system health indicators and notifications, and some network and display configuration options
- the sidebar allows navigating between pages, and allows restarting, freeing up space, and reporting issues
- most pages show their content within the BlueOS interface sections, but some extensions open as full pages in a separate tab

For more details see the Advanced Usage [Interface Overview](../advanced-usage/#interface-overview) section.

## Updating / Releases

BlueOS supports [multiple release types](../overview/#release-types) - we recommend the latest stable version for most people. Releases and change-logs are available on the [GitHub releases page](https://github.com/bluerobotics/blueos-docker/releases).

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

1. Click on the hamburger menu (if the sidebar is not already open)

   ![Version Menu](version-menu.png)
1. Under **Settings**, select [**BlueOS Version**](../advanced-usage/#blueos-version)

   ![Version Chooser](version-chooser.png)
1. If you're already on the latest version, the right side of your Local Version will be blank. If not, you should see a blue **Update** button.

   <img src="../advanced-usage/version-chooser-simple.png" width="550">
1. Once the update button is clicked the update process will run.
   Please wait until it finishes - it will automatically reload the webpage for you.

## Camera Streams

BlueOS is capable of configuring and streaming multiple cameras simultaneously. The first time it boots, it will automatically detect any connected H264-capable cameras and start streaming them. If not, make sure your camera is properly connected, and that BlueOS is on the latest available version. Reset settings and restart BlueOS if necessary.

Additional information is available in the Advanced Usage [Video Streams](../advanced-usage/#video-streams) section.
