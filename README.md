# ARM Samba Server Container

[![Docker Pulls](https://img.shields.io/docker/pulls/zatrac/docker-samba-server.svg)](https://hub.docker.com/r/zatrac/docker-samba-server/)
[![Docker Stars](https://img.shields.io/docker/stars/zatrac/docker-samba-server.svg)](https://hub.docker.com/r/zatrac/docker-samba-server/)
[![Docker Build](https://img.shields.io/docker/automated/zatrac/docker-samba-server.svg)](https://hub.docker.com/r/zatrac/docker-samba-server/)
[![Docker Build Status](https://img.shields.io/docker/build/zatrac/docker-samba-server.svg)](https://hub.docker.com/r/zatrac/docker-samba-server/)

[Samba 4](https://www.samba.org/) server running under [s6 overlay](https://github.com/just-containers/s6-overlay) on [ARMHF Alpine Linux](https://hub.docker.com/r/arm32v6/alpine/). Runs both `smbd` and `nmbd` services. 
Compatible with Raspberry Pi.

## Configuration

See [example directory](https://github.com/Zatrac/docker-samba-server/tree/master/example) for sample config file.

## Quickstart

```yml
samba:
  image: zatrac/docker-samba-server

  volumes:
    # You must provide a Samba config file
    - ./smb.conf:/etc/samba/smb.conf

    # Shares
    - ~/projects:/mnt/projects
    - ~/videos:/mnt/videos:ro

  ports:
    - "137:137/udp"
    - "138:138/udp"
    - "139:139/tcp"
    - "445:445/tcp"

  environment:
    - USERNAME=joe
    - PASSWORD=samba
```
