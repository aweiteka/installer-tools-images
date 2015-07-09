# Ansible base container image

This is a base image containing the ansible client. It may be used stand-alone but it is more useful for using as a base image to layer your playbooks on.

## Use

### As a base image

1. In your ansible repository create a Dockerfile built on this image and add your playbooks.

        FROM aweiteka/ansible-client
        MAINTAINER <you@example.com>

        ADD <repo/path/to/playbooks> /root/ansible-playbooks/

1. Build and ship the container image to your users.

### Standalone

1. Change to a directory of ansible playbooks.
1. Run this image. You will be dropped into the container shell.

        atomic run aweiteka/ansible-client

1. Execute ansible commands. The playbooks from your host are bindmounted to the current working directory. For example:

        ansible-playbook myplaybook.yaml

## Design

There are several design challenges in specifying how this image is run. Here are the choices made:

1. Bindmount private key `~/.ssh/id_rsa`. This may not be desired.
1. Bindmount `/etc/ansible/hosts`. This may not be desired.
1. Use `--net=host` so the container `/etc/hosts` matches the host. This may not be desired.

## Why

This approach solves two problems.

1. Simple packaging for ansible metadata files. Users will not have to clone repositories to get files.
1. No need to install ansible client to try out your software.
