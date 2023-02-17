+++
title = "Installation"
description = "BlueOS installation instructions."
date = 2023-02-17T22:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
aliases = ['/software/onboard/BlueOS-latest/installation']

[extra]
toc = true
top = false
+++
## Download

BlueOS is a ground-up rewrite software to replace Companion. To use it you'll need to download and flash an SD card.
It is compatible with both **Raspberry Pi 3** and **Raspberry Pi 4**.

The latest available stable version is:
- [1.0.1](https://github.com/bluerobotics/BlueOS-docker/releases/download/1.0.1/BlueOS-raspberry.zip) (06-april-2022)

## Flash

We recommend using a fresh SD card, with at least 4GB capacity.

1. Download and install [Balena Etcher](https://www.balena.io/etcher/)
1. Insert the SD card to your computer (you may need an SD card reader)
1. Open Etcher, select the image you just downloaded, and flash it onto the SD card

## Run

1. Eject your SD card with the new BlueOS software
1. Insert it into your Raspberry Pi, and power it up!
   - The first boot may take a couple of minutes, as it expands the filesystem to the new SD card capacity
      - It should take around 2 minutes for a 16GB class 10 SD card
1. BlueOS is a _headless_ operating system, and uses a web interface rather than HDMI to a monitor
   - See the [Getting Started](./getting-started/) section for how to connect


## Updates

Once BlueOS is installed, updating to a different version is simple via the [Version Chooser](./advanced-usage/#blueos-version).

## Manual Installation

For developers with alternative hardware, or who would rather install over a pre-installed base operating system / image, BlueOS provides an [install directory](https://github.com/bluerobotics/BlueOS-docker/tree/master/install) with utilities to help perform manual/software-based installations.
