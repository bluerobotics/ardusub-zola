+++
title = "Contributing"
description = "Contribution Guidelines."
date = 2022-09-13T22:27:00+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 0
draft = false
[extra]
lead = 'Our software and documentation are open for contributions - join us in developing the future!'
toc = true
top = false
+++

## Contribution Pathways

- [Blue Robotics](https://github.com/bluerobotics/software-guidelines)
- [ArduPilot](https://ardupilot.org/dev/docs/contributing.html)
   - [Top Contributors](https://github.com/ardupilot/ardupilot#top-contributors)
   - [How to Get Involved](https://github.com/ardupilot/ardupilot#how-to-get-involved)
- [QGroundControl](https://dev.qgroundcontrol.com/master/en/contribute/)
- [MAVLink](https://mavlink.io/en/contributing/contributing.html)

## This Documentation

Add a new section / version via a repository/branch as a submodule
```
git submodule add -b <branch-name> --name <section-name> <repository url> <path/to/desired/location>
```

### In General
1. Fork the repo
1. make a new branch for development
1. submit a pull request to the original repo
1. make changes as relevant
1. clean up commits with an interactive rebase and force push
1. sync your repo branch with the upstream branch once the PR is merged
