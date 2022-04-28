+++
title = "Installation"
description = "Companion Docker installation instructions."
date = 2021-10-20T20:30:00+00:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
[extra]
lead = 'Now with a stable release! Be aware that if you have a <strong>B.E.T.A</strong> before <strong>1.0.0 release</strong> a fresh SD card flash is necessary.'
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

The first boot may take a couple of minutes, as it expands the filesystem to the new SD card capacity. It should take around 2 minutes for a 16GB class 10 SD card.

## Updates

Once BlueOS is installed, updating to a different version is simple.

The BlueOS Version Chooser offers several major robustness and versatility improvements over the previous 'latest update only' approach, which should benefit both users and developers:
- it supports multiple [release types](../overview/#release-types)
- it supports changing forwards _and backwards_ between versions
- previously installed versions are stored locally, and can be easily switched between
- it is less likely to fail during an update
- it is better at detecting and resolving failures that occur
- if an undetected failure somehow occurs (or if a broken version gets installed) it's possible to easily roll back to a working version from on the device, manual upload, or downloaded from the internet
- it runs independently, so is still available even in an extreme case like the main web interface being broken
