# Docker Files

This repository contains configuration files used to generate [Docker] images
registered on [Dockerhub].

## Usage

Check out the [Docker docs] for information on working with images.

Each image is pushed to the thoughtbot organization on Dockerhub. You can
install an image using `docker pull`:

    docker pull thoughtbot/yesod-bin

You can use an image as a base image in a `Dockerfile`:

    FROM thoughtbot/yesod

## Editing

To update an image:

1. Edit the appropriate Dockerfile, for example `haskell/yesod/Dockerfile`
2. Build it locally: `docker build -t thoughtbot/yesod:YESOD_VERSION-BUILD_VERSION`
  * `YESOD_VERSION` should be kept up to date. Currently at 1.4.10.
  * `BUILD_VERSION` is out our incrementing verison of builds.
  * Also tag a `latest` release: `docker tag thoughtbot/yesod:YESOD_VERSION-BUILD_VERSION thoughtbot/yesod:latest`
3. Push it up to docker using `docker push thoughtbot/yesod`

Everybody has their own Dockerhub account. If you need to be invited to the
thoughtbot organization, just ask.

[Docker]: https://www.docker.com/
[Dockerhub]: https://registry.hub.docker.com/repos/thoughtbot/
[Docker docs]: https://docs.docker.com/userguide/dockerimages/
