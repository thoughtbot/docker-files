# Bourbon Docker image

This image contains the sass binary and provides Bourbon.

## Usage

The image looks for sass files in a `/src` directory and outputs css files in a
`/build` directory. To build your Bourbon-based sass project:

    docker run \
      --rm \
      -v $PWD/sass:/src \
      -v $PWD/public/stylesheets:/build \
      -t thoughtbot/bourbon

The default command (above) builds all updated sass files, but you can also
watch for changes:

    docker run \
      --rm \
      -v $PWD/sass:/src \
      -v $PWD/public/stylesheets:/build \
      -t thoughtbot/bourbon \
      --watch /src:/build

## Using Docker Compose

You can add a css service to your `docker-compose.yml` to watch for changes in
development:

```
css:
  image: thoughtbot/bourbon:latest
  command: --watch /src:/build
  volumes:
    - sass:/src
    - public/stylesheets:/build
```

Start watching by running `docker-compose`:

    docker-compose start css

Changes to your sass files will be picked up by the service in the Docker
container and written to your static directory.

You can build everything for deployment:

    docker-compose run css --update /src:/build
