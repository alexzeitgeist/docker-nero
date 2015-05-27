# zeitgeist/docker-nero

[Nero Linux](http://www.nero.com/enu/promo-linux.html) in a Docker container.

## Requirements

* [Docker](https://www.docker.com/) 1.6+ (previous versions may work fine, but I haven't tried)
* An X11 socket

## Installation

Get the [trusted build on the docker hub](https://registry.hub.docker.com/u/zeitgeist/docker-nero/):

```bash
$ docker pull zeitgeist/docker-nero
```

or download and compile the source yourself from Github:

```bash
$ git clone https://github.com/alexzeitgeist/docker-nero.git
$ cd docker-nero
$ docker build -t zeitgeist/docker-nero .
```

## Usage

```bash
$ xhost +

docker run --rm \
  -v /etc/localtime:/etc/localtime:ro \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -e DISPLAY=unix$DISPLAY \
  --privileged \
  -v /dev/snd:/dev/snd \
  -v /dev/sr0:/dev/sr0 \
  -v "${HOME}/temp":"/home/user/temp" \
zeitgeist/docker-nero
```

Where ${HOME}/temp is a shared volume from your host and /dev/sr0 your cdr device.

* [Nero Linux 4 Manual](http://ftp6.nero.com/user_guides/linux4/NeroLinux_Eng.pdf)
