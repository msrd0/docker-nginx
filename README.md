[![](https://images.microbadger.com/badges/image/msrd0/nginx.svg)](https://microbadger.com/images/msrd0/nginx "Get your own image badge on microbadger.com") ![](https://img.shields.io/docker/pulls/msrd0/nginx.svg)

# Super Lightweight nginx Image

`docker run -v /srv/web:/static -p 80:80 msrd0/nginx`

This command exposes an nginx server on port 80 which serves the folder `/srv/web` from the host.

The image is roughly half the size of the official nginx image and can only be used for static file serving.

This image, unlike the official nginx alpine docker image, is capable of handling IPv6 connections.

## Custom Configuration

If you are not satisfied by just serving static files, you can copy or mount your own `nginx.conf` into the container:

`docker run -v ./nginx.conf:/etc/nginx/nginx.conf -p 80:80 msrd0/nginx`

### nginx via HTTPS

I recommend to use this image in conjunction with [msrd0/dehydrated](https://hub.docker.com/r/msrd0/dehydrated/) to automate
getting certificates from Let's Encrypt.

### nginx-static with docker-compose

```
version: '3'
services:
  example.org:
    image: msrd0/nginx
    container_name: example.org
    ports:
      - 80:80
    volumes:
      - /srv/web:/static
```
