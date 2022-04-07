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

BlueOS is a ground-up rewrite software to replace Companion, to use, it's necessary downloaded and flash an SD card.
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
