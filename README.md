# Ingress

A simple webserver for our services running at the hackerspace.

## Description

This service is a central proxy that makes your applications automatically accessible over HTTP(S). It connects to the Docker socket and dynamically reconfigures itself. 

## Usage

Add Ingress to your cluster by creating another stack:

```
$ docker stack deploy --compose-file docker-compose.yml ingress
```

Then add add a label you your application's Compose file. Example:

```
---

version: '3'

services:
  backend:
    image: labello
    build: .
    labels:
      - "traefik.frontend.rule=Host: labello.chaosdorf.space"
```

## Building

Build the image by running `docker-compose build` or just use the public image on [Docker Hub](https://hub.docker.com/r/chaosdorf/ingress/)

## Further Information

 - The traefik project: [traefik.io](https://traefik.io/)
