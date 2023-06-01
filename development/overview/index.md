+++
title = "Overview"
description = "BlueOS development overview."
date = 2023-06-01T19:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 10
draft = false
aliases = ['software/onboard/BlueOS-latest/development/overview']

[extra]
lead = ''
toc = true
top = false
+++

## Technology Stack

### Structure

{{ easy_image(src="blueos-structure", width=450) }}

Conceptually, BlueOS is structured around 4 main components:

1. [Bootstrap](#bootstrap)
1. [Core](#core)
1. [Extensions](#extensions)
1. [Cloud](#cloud-infrastructure)

### Development Infrastructure

To understand how BlueOS is developed, it's valuable to understand what it's made of, and the ideas it has been designed around:

- Containerised components and services ([Docker](#docker))
    - Containerised, individual services are easier to maintain than a monolithic system
    - Can restart and update containers with very low risk of needing to re-flash SD card
    - Integrators can create their own [Extensions](#extensions), instead of forking the whole system
        - Allows Extension and BlueOS version changes without affecting the underlying system
    - Dependencies are isolated, so individual services don’t need to compete for versions
    - Access to system and hardware resources can be limited per Extension
- Web interfaces and APIs
    - Core interface provides consistency, control, and displays active services
    - Services display links to API documentation → simplifies development
    - [Extensions Manager](../../advanced-usage#extensions-manager) makes it easy to find, install, and manage services from others
        - Includes a web store, where Extensions can be downloaded from
- Frontend (Vue.js, Typescript)
    - Allows for very reactive components (see heartbeats icon)
    - Using reusable Vuetify components to make it look good
    - Relies heavily on [Mavlink2Rest](https://github.com/mavlink/mavlink2rest) (rust-mavlink) for integrating MAVLink with web technologies
- Modern backend technologies
    - Python (3.9) for simple services
    - Rust used for critical services
    - MAVLink-Router for MAVLink routing

#### Docker

[Docker](https://www.docker.com/resources/what-container/) is a lightweight containerisation system that allows packaging one or more software programs into a single executable that can be easily shared across systems. A static package is referred to as a "Docker Image", and when it is being run it takes the form of a "Docker Container".

A Docker Container generally acts like an isolated mini operating system, but it's possible to enter a running Container from the host computer to see (and modify) what the programs inside are doing, and access things like logging output. Importantly, changes in a Container do not affect its [Image](https://docs.docker.com/get-started/overview/#images), so they're not persistent[^1] and it's possible to "start fresh" by simply restarting the Container (which creates a new Container from the Image, without any changes from previous instances).

[^1]:While changes _within_/_to_ the Container are not persistent, it is possible to make persistent changes to the host's file-system if the Container has access to it (usually via `"HostConfig": "Binds"` in the [metadata](../extensions#metadata-dockerfile) `permissions`, or [volumes](https://docs.docker.com/storage/volumes/)).

### Bootstrap

[BlueOS-bootstrap](https://github.com/bluerobotics/BlueOS-docker/tree/master/bootstrap) is responsible for making sure [BlueOS-core](#core) is running as expected, as well as gracefully restarting core during BlueOS updates and if it is detected to have unexpectedly stopped/crashed. For an update the current core image gets shut down and the newly installed image gets started in its place, whereas in the case of a crash bootstrap reverts to running a known working core image, which is currently the one tagged as `factory` (which is whatever it was first flashed with), so that it's at least possible to access the interface.

### Core

[BlueOS-core](https://github.com/bluerobotics/BlueOS-docker/tree/master/core) is the body of BlueOS, and runs all of the built in [services](../../advanced-usage#available-services), along with the main web interface.

### Extensions

BlueOS has support for [Extensions](../extensions), which are handled by the [Extensions Manager](../../advanced-usage#extensions-manager) service in core. Extensions are individual Docker images that run independently of BlueOS, but can hook into the core systems and host system, providing access to additional devices and data streams, as well as modifying / adding to the web interface.

### Cloud Infrastructure

While BlueOS itself runs locally on the vehicle, there are various cloud-based services involved that allow downloading new BlueOS releases, installing new autopilot firmware, and finding and installing available extensions.

## Developer Presentations

### BlueOS Development Features
`ArduPilot Developers Unconference (March 2023)`
<iframe width="560" height="315" src="https://www.youtube.com/embed/61pHgPzhHv8" title="YouTube video player" frameborder="0" allow="encrypted-media;" allowfullscreen></iframe>

### Introduction to BlueOS
`ArduPilot Developers Unconference (April 2022)`
<iframe width="560" height="315" src="https://www.youtube.com/embed/eV6oDm6He2U" title="YouTube video player" frameborder="0" allow="encrypted-media;" allowfullscreen></iframe>
