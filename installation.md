+++
title = "Installation"
description = "Cockpit installation instructions."
date = 2023-08-25T12:00:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
aliases = ['/software/control-station/Cockpit-latest/installation']

[extra]
toc = true
top = false
+++

## BlueOS Extension

For vehicles with an [Onboard Computer](@/hardware/required/onboard-computer/index.md) running [BlueOS](https://blueos.cloud/docs/blueos),
and an IP-based (wifi / ethernet tether) connection to the [Control Station Computer](@/hardware/required/control-computer/index.md),
Cockpit [is available](https://docs.bluerobotics.com/BlueOS-Extensions-Repository/#:~:text=Cockpit,-Maintainer)
as a [BlueOS Extension](https://blueos.cloud/docs/blueos/latest/extensions).

### Updates

Once installed, updating to a new Cockpit version can be done via the "Installed" tab of the BlueOS
[Extensions Manager](https://blueos.cloud/docs/blueos/latest/advanced-usage/#extensions-manager).


## Self-Contained Application

In future, Cockpit will also be available as a self-contained Electron application, which can be stored on a Control Station
Computer and started up for connection to a vehicle.
