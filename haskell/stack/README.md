# Stack Docker Image

A base image with Stack installed.

## Usage

Create your own `Dockerfile` inheriting from this image:

```
FROM thoughtbot/stack
```

Here's a sample `bin/deploy` script you can use in your Heroku project, assuming
you already have the heroku-docker Heroku plugin installed:

```sh
#!/bin/sh

set -e

if (( $# != 1 )); then
  echo "Usage: ./bin/deploy (staging|production)"
  exit 1
fi

if [ $(uname) == "Darwin" ]; then
  eval "$(docker-machine env default)"
fi

heroku docker:release --remote "$1"
heroku open --remote "$1"
```
