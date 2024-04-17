+++
title = "BlueOS-bootstrap"
description = "BlueOS-bootstrap development documentation."
date = 2023-12-04T19:30:00+11:00
template = "docs/page.html"
sort_by = "weight"
weight = 20
draft = false

[extra]
lead = ''
toc = true
top = false
+++

## Function

BlueOS-bootstrap is responsible for making sure [BlueOS-core](../core) is running as expected, as well as gracefully restarting core during BlueOS updates and if it is detected to have unexpectedly stopped/crashed. 
For an update the current core image gets shut down and the newly installed image gets started in its place, whereas in the case of a crash bootstrap reverts to running a known working core image, which is currently the one tagged as `factory` (which is whatever it was first flashed with), so that it's at least possible to access the interface.

## Codebase

[BlueOS-bootstrap](https://github.com/bluerobotics/BlueOS/tree/master/bootstrap) is open source, and lives within the broader [BlueOS](https://github.com/bluerobotics/BlueOS) GitHub repository. [Issues](https://github.com/bluerobotics/BlueOS/issues) can be used to report bugs or suggest features, and [Pull Requests](https://github.com/bluerobotics/BlueOS/pulls) fixing bugs or adding new features are welcomed.

BlueOS is set up with a [GitHub Action](https://docs.github.com/en/actions) that [automatically builds and deploys](https://github.com/bluerobotics/BlueOS/blob/master/.github/workflows/test-and-deploy.yml#L90) a BlueOS-bootstrap image when changes are pushed to the GitHub repository.
If you want to make use of that functionality you'll need a [DockerHub](https://hub.docker.com) account, and will need to specify your DockerHub username (`DOCKER_USERNAME`) and password (`DOCKER_PASSWORD`) in your fork's [GitHub secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets).

## Updating

{% warning() %}
BlueOS-bootstrap is a critical component of running BlueOS, and can significantly affect the system stability. It should only be updated when necessary, and preferably at times where the onboard computer hardware is accessible in case something goes wrong. For normal users it is strongly recommended to only update BlueOS-bootstrap to match stable releases of BlueOS, and even then only if there is a known issue an update is expected to fix or improve.
{% end %}

BlueOS-bootstrap versions are built at the same time as BlueOS-core versions, and they get bundled together in the Raspberry Pi images that can be flashed onto an SD card to install BlueOS onto it. For official BlueOS releases it is possible to update the BlueOS-bootstrap image to match the BlueOS release through the [BlueOS Version](../../advanced-usage#blueos-version) chooser, and is the recommended process.

Manually updating to a non-matched and/or custom bootstrap image requires using the [Terminal](../../advanced-usage#terminal):

```sh
# drop down from blueos-core into the underlying operating system:
red-pill
# get the running bootstrap container id
CURRENT_BOOTSTRAP_CONTAINER=$(docker ps -aq --filter name=blueos-bootstrap)
# stop the bootstrap container (takes 10 seconds)
docker stop $CURRENT_BOOTSTRAP_CONTAINER
# remove the container from local memory
# (the underlying image remains on the system, unused)
docker container rm $CURRENT_BOOTSTRAP_CONTAINER
# specify the Docker image source (use your account if testing a change)
BOOTSTRAP_REPO=bluerobotics
BOOTSTRAP_IMAGE=blueos-bootstrap
# specify the new version to use (e.g. 1.1.0-beta.27, or master)
NEW_BOOTSTRAP_VERSION=1.1.0-beta.27
# start running the new version
# (will automatically download if it's not already available locally)
docker run \
    -d -t \
    --restart unless-stopped \
    --name blueos-bootstrap \
    --net=host \
    -v /root/.config/blueos/bootstrap:/root/.config/bootstrap \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -e BLUEOS_CONFIG_PATH=/root/.config/blueos \
    $BOOTSTRAP_REPO/$BOOTSTRAP_IMAGE:$NEW_BOOTSTRAP_VERSION
# view the logs, to check for any error or progress messages
docker logs -f $BOOTSTRAP_IMAGE
# press ctrl+c to return to the terminal, and you're done
# if you want, type 'exit' or 'logout' to return to the BlueOS-core container
```
