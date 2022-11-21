+++
title = "Pymavlink"
description = "Examples of using Pymavlink for programmatic control."
date = 2022-06-13T14:50:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
[extra]
lead = 'Pymavlink is a Python implementation of the MAVLink protocol. It can be used to read sensor data and send commands to an ArduSub vehicle.'
toc = true
top = false
+++

# Safety
- pilot input (`FS_PILOT_INPUT`)
- leak
- heartbeat
- rc timeout (`RC_OVERRIDE_TIMEOUT`)

# Installation
...

# Examples

Pymavlink has 3 types of messages:
* `command_long_send`: To create a raw package
* `<message_name>_send`: To send simple mavlink messages
* `mavutil`: Functions to abstract some MAVLink messages

## Connecting

### Serial Connection
### Onboard Computer
### Topside Computer

## High Level
### Periodic Events
### Command Protocol

## Controlling the Vehicle
### Send RC
- ArduPilot based around radio-style control
- Inputs are set as PWM channel values
- Ignore a channel via int16_max (65535), but warn that previous value persists
### Send Manual Control (Joystick)
- Abstraction over control aspect
- Can pretend to be a pilot
- Link to joystick functions
- Underlying functionalities generally have explicit messages (link to(/implement?) command protocol)
- All axes must be specified (link to issue of ArduSub not supporting the "ignore" value)
### Arm/disarm
- Vehicle cannot move without arming
### Change flight mode
- Link to flight mode docs
### Set Target Depth/Attitude
- In depth hold/stabilise modes, ArduSub will use control algorithms
- Mention caveats (maximum depth delta, target ignored/reset if vehicle control is actively commanding)
### Control Camera Gimbal
- Via mount commands
- Via servo PWM
- Via RC input (goes to full extent, value specifies speed)
### Set Servo PWM
- Only works for servos that aren't assigned as motors (possibly no function specified?? - confirm)
### Advanced Servo/Gripper Example

## Accessing Parameters
### Read all parameters
### Read and write parameters

## Receiving Data
### Request message interval
- Required for many messages
- TODO: investigate how to receive for `NAMED_VALUE_FLOAT` (request stream?)
- QGC requests a bunch by default, so if it's open then you'll already be receiving several messages (and may not be able to specify rates)
### Receive data and filter by message type
### Advanced Receiving (Message Hooks)

## Sending Data
### Send Message to Ground Control Station
### Send GPS position
### Send rangefinder / computer vision distance measurement to autopilot
