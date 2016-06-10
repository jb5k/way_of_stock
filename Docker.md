# Docker

[Docker](https://www.docker.com/) is the container management solution we are starting to use. It will become
the mechanism via which all of our applications are packaged and installed.

## Getting Started

Docker is an active project and rather than trying to replicate the instructions, the source website
is the best place to go look for instructions. There are specific instructions for [Linux](https://docs.docker.com/linux/),
[OSX](https://docs.docker.com/mac/) and [Windows](https://docs.docker.com/windows/). There is also a reasonably
useful [cheat-sheet](https://github.com/wsargent/docker-cheat-sheet) that may be available [locally](../docker-cheat-sheet/README.md).

The remaining section adds some additional notes that should help you getting started.

## Creating a local Docker Machine

Docker machine is the mechanism via which we will configure hosts to run docker containers. During
development you will most likely use VirtualBox to host the docker engine and deploy into the virtual
box host. The simplest way to create such a host is:

    $ docker-machine create --driver virtualbox default

However this may not be needed as the machine can be created when the latest docker toolbox is installed.

The machine can be started and stopped via the commands

    $ docker-machine stop default
    $ docker-machine start default

To get your local docker commands to communicate with this docker engine instance you will need to set
up some environment variables. This can be done via:

    $ eval $(docker-machine env default)

## Building an image

Assuming you are creating a docker image from a Dockerfile in a directory it is as simple as:

    $ docker build -t image_name path/to/dir

## Running an image

Images can be turned into running containers. There is a whole range of parameters that can be passed
to the run sub-command but a typical command is:

    $ docker run --rm --name my_container -i -t stocksoftware:ruby bash

# Bash Completion

    $ brew install bash-completion
    $ echo ". $(brew --prefix)/etc/bash_completion" >> ~/.bash_profile
    $ wget https://raw.githubusercontent.com/docker/docker/master/contrib/completion/bash/docker -O ~/.docker_completion.sh
    $ echo ". ~/.docker_completion.sh" >> ~/.bash_profile

# Configuring DNS correctly for Docker for Mac

To get the set of DNS servers that are available on OSX the easiest command to determine this is `scutil --dns`.
This will give several pagefuls of information, particularly if you are attached to multiple networks such as
via a VPN. The "correct" DNS server should be selected where correct determines which network you want to resolve
using. Often it is the one on the VPN network. A simpler command to list all DNS servers is

    $ scutil --dns | grep 'nameserver\[[0-9]*\]' | awk '{print $3}' | grep -v '::' | sort | uniq

It should be noted that it is hoped that a future version of docker should eliminate the need for all this setup
but it is currently required.

## Build-time DNS

To set the build-time DNS follow these steps:

1) Access the terminal of the Docker Alpine VM using GNU screen:

    $ screen ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/tty

2) Login as user root. No password necessary

3) Edit /etc/hosts and/or /etc/resolv.conf to point to dns resovlers inside the VPN.

4) To quit the screen app, type CTRL-A, then CTRL-\\

## Run-time DNS

Runtime dns can be specified by passing the `--dns DNS` parameter to the `docker run` command. If you are
using Redfish the easiest way to ensure this happens is to set the environment variable `DOCKER_DNS`.

# Useful commands

### Get IP address

    docker inspect -f '{{ .NetworkSettings.IPAddress }}' <container_name>

### Delete Stopped containers

    docker rm -v $(docker ps -a -q -f status=exited)

### Delete old containers

  docker ps -a | grep 'weeks ago' | awk '{print $1}' | xargs docker rm

### Delete Dangling images

    docker rmi $(docker images -q -f dangling=true)

### Delete dangling volumes

  docker volume rm $(docker volume ls -q -f dangling=true)

### Kill running containers

    docker kill $(docker ps -q)

### Monitor system resource utilization for running containers

    docker stats <container>

or for all containers

    docker stats

or for all containers by name

    docker stats $(docker ps --format '{{.Names}}')

### List images based on ancestor

    docker ps -a -f ancestor=stocksoftware/redfish
