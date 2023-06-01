+++
title = "BlueOS-core"
description = "BlueOS-core development documentation."
date = 2023-06-01T19:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
aliases = ['software/onboard/BlueOS-latest/development/core']

[extra]
lead = ''
toc = true
top = false
+++

## Codebase

[BlueOS-core](https://github.com/bluerobotics/BlueOS-docker/tree/master/core) is open source, and lives within the broader [BlueOS-docker](https://github.com/bluerobotics/BlueOS-docker) GitHub repository. [Issues](https://github.com/bluerobotics/BlueOS-docker/issues) can be used to report bugs or suggest features, and [Pull Requests](https://github.com/bluerobotics/BlueOS-docker/pulls) fixing bugs or adding new features are welcomed.

## Contributions

### Adding a Flight Controller

Adding USB detection support for a new type of [flight controller board](@/hardware/required/flight-controller/index.md) is reasonably straightforward, but does require a few different steps:

#### Find the USB device information

1. Connect your flight controller board via USB[^2] to a computer running BlueOS
1. Go to the BlueOS [Terminal](../../advanced-usage#terminal) page
1. Open a Python console (run the `python3` command)
1. Run `from serial.tools.list_ports import comports`
1. Run `from pprint import pprint`
1. Run `[pprint(port.__dict__) for port in comports()]`
1. Get the `"product"` and `"manufacturer"` values for your flight controller board

[^2]:Non-USB serial connections are [not yet supported](https://github.com/bluerobotics/BlueOS-docker/issues/1615).

#### Find the flight controller hardware information

1. Go to [the ArduPilot hardware definition files](https://github.com/ArduPilot/ardupilot/tree/master/libraries/AP_HAL_ChibiOS/hwdef)
1. Find the folder corresponding to your flight controller board
1. Find the `APJ_BOARD_ID` variable in the `hwdef.dat` or `hwdef.inc` file

#### Add the board, and confirm it works

1. Fork the [BlueOS-docker](https://github.com/bluerobotics/BlueOS-docker) repository
    - You'll need a GitHub account to do this
1. Click where it says `master`, and create a new branch (e.g. `add-pixhawk-6C`)
1. Navigate to `core/services/ardupilot_manager/typedefs.py` and add your board's name and type to the `Platform` class
    - Use `PlatformType.Serial` for USB/serial connections - `Linux` is reserved for sensor/peripheral expansion boards that run the autopilot firmware directly on the [Onboard Computer](@/hardware/required/onboard-computer/index.md)
1. Navigate to `core/services/ardupilot_manager/flight_controller_detector/board_identification.py` and add appropriate `SerialBoardIdentifier` instances to the `identifiers` list (using the "product" and "manufacturer" values from earlier)
    - The "product" is more important/useful, because one "manufacturer" can make multiple different board types
1. Navigate to `core/services/ardupilot_manager/firmware/FirmwareInstall.py` and add your board to the `get_board_id` function (using the `APJ_BOARD_ID` value from earlier)
1. If you did your code modifications in GitHub skip to the next step - if you're editing the files in a local clone make sure to `git commit` and `git push` back up to your GitHub fork of the repository
1. GitHub should prompt you that there are recent changes in your new branch - click the prompt to submit a Pull Request to the upstream Blue Robotics repository
    - The "files" tab of your pull request should look similar to [this example](https://github.com/bluerobotics/BlueOS-docker/pull/1067/files)
1. Wait for the GitHub actions to complete (at the bottom of your pull request), then find [the build action](https://github.com/bluerobotics/BlueOS-docker/actions/workflows/test-and-deploy.yml) corresponding to your branch, and download the `BlueOS-core-docker-arm-v7` artifact from it
1. Go to the BlueOS [Version Chooser](../../advanced-usage/#blueos-version), scroll down to the bottom, and "manual upload" the artifact you downloaded
1. Once BlueOS has restarted, see whether the flight controller board is being detected as an autopilot in the [Autopilot Firmware](../../advanced-usage/#autopilot-firmware) page
