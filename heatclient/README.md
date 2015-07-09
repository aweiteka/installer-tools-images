# OpenStack Heat client container image

This is a base image containing the OpenStack heat client. It may be used stand-alone but it is more useful for using as a base image to layer your heat templates on.

## Use

### As a base image

1. In your heat template repository create a Dockerfile built on this image and add your heat templates.

        FROM heatclient
        MAINTAINER <you@example.com>

        ADD <repo/path/to/templates> /root/heat-templates/

1. Build and ship the container image to your users.

### Standalone

1. Change to a directory of heat template(s).
1. Run this image. You will be dropped into the container shell.

        atomic run heatclient

1. Execute heat commands. The heat templates from your host are bindmounted to the current working directory. For example:

        heat stack-create -f my-template.yaml -e my-params.yaml my-stack

## Why

This approach solves two problems.

1. Simple packaging for heat template metadata files. Users will not have to clone repositories to get templates or install template files using traditional packaging such as RPM.
1. No need to install heat client to try out your software.
