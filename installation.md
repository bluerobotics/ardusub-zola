+++
title = "Installation"
description = "Companion Docker installation instructions."
date = 2021-10-20T20:30:00+00:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
[extra]
lead = 'Be aware that <strong>B.E.T.A may not be stable</strong> and <strong>changes will occur</strong> during the development.'
toc = true
top = false
+++
## Download

The new Companion is a ground-up rewrite, so needs to be downloaded and flashed to an SD card. 
It is compatible with both **Raspberry Pi 3** and **Raspberry Pi 4**, so choose your poison.

The latest available beta image is:
- [1.0.0.beta1](https://s3.amazonaws.com/downloads.bluerobotics.com/Pi/experimental/companion-docker-15-oct-2021-1.0.0-beta1.img.zip) (15-oct-2021)

## Flash

We recommend using a fresh SD card, with at least 4GB capacity.

1. Download and install [Balena Etcher](https://www.balena.io/etcher/)
1. Insert the SD card to your computer (you may need an SD card reader)
1. Open Etcher, select the image you just downloaded, and flash it onto the SD card

## Run

1. Eject your SD card with the new Companion software
1. Insert it into your Raspberry Pi, and power it up!

The first boot may take a couple of minutes, as it expands the filesystem to the new SD card capacity. It should take around 2 minutes for a 16GB class 10 SD card.
