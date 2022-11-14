+++
title = "Extensions (Alpha)"
description = "BlueOS extensions documentation."
date = 2022-11-15T00:20:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 40
draft = false
[extra]
lead = ''
toc = true
top = false
+++

## Context

- https://discuss.bluerobotics.com/t/external-integrations-extensions/10912
- future plans and reasoning

## Implementation

### Docker Images

### Extensions Manager (Local)

Currently:
- Install extensions from store
- Runs installed extensions on startup
- Track CPU and memory usage (per extension)
- View extension logs
- Uninstall extensions that are no longer wanted (technically disable)
- Manually update extensions

Planned:
- Disable extension (explicitly)
- Support automatic extension updates
- Manage/edit permissions
- Allow restarting extensions
- Create a custom extension configuration
- Uninstall -> remove image (proper cleanup)

### Extensions Repository (Online Store)

- https://github.com/bluerobotics/BlueOS-Extensions-Repository

## Developing an Extension

### Requirements

- Register service -> web interface shows up in the sidebar menu
- Dockerfile -> metadata for the manifest that allows the extension to be found and installed, and provides the entrypoint to run the extension -> runs at build time (build recipe)
- build tag and upload to docker hub
- Code that actually does/shows something
   - python to run stuff
   - static html to contain stuff
- Test extension by doing manual configuration (specify location of docker image, including tag)
- To register an extension for installation, need to submit PR to BlueOS-Extensions-Repository
   - requires semver tag (explain) in order to be detected by manager

### Process

- development-process.mermaid (expandable section??)
- add details for important steps

### Examples

- https://github.com/Williangalvani/BlueOS-examples
