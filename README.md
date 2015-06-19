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

To update an image, edit the appropriate Dockerfile, build it locally, and push
a new version to Dockerhub.

Everybody has their own Dockerhub account. If you need to be invited to the
thoughtbot organization, just ask.

[Docker]: https://www.docker.com/
[Dockerhub]: https://registry.hub.docker.com/repos/thoughtbot/
[Docker docs]: https://docs.docker.com/userguide/dockerimages/
