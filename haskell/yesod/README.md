# yesod docker image

Use this image as the base image for your yesod based applications.

## Usage

The simplest usage is to create a `Dockerfile` for your project that looks like
this:
```
FROM thoughtbot/yesod

RUN mkdir -p /app
WORKDIR /app

COPY *.cabal ./
RUN cabal install --dependencies-only -j4 --enable-tests
```

## Setup Your Yesod Project

First, create a `Dockerfile` for your project. The one shown above is a good
starting place.

Yesod needs some sort of database backend as well. We can setup a postgresql or
other database dependency using [docker-compose].

[docker-compose]: https://docs.docker.com/compose/install/

Create a `docker-compose.yml` file inside your project. A simple setup might
look like this:

```
db:
  image: postgres:9.4
  ports:
   - "5432"
web:
  build: .
  command: yesod devel
  environment:
    - HOST=0.0.0.0
    - PGUSER=postgres
    - PGPASS
    - PGHOST=db
  stdin_open: true
  volumes:
   - .:/app
  ports:
   - "3000:3000"
  links:
   - db
```

Build everything with `docker-compose build`.

Now create your app database by running:

```
docker-compose run web createdb -h db -U postgres DATABASE_NAME
```

Where `DATABASE_NAME` is the name of your database specified in your
`config/settings.yml`.

Finally, run your project with `docker-compose up`.

Your project should spin up and yesod will compile and run. You can now edit
files on your machine and yesod will recompile every time a file changes.

### Testing

You can run your tests anytime with `docker-compose run web yesod test`;
however, you'll have to create your test database first. Similarly to how
we created our app database, you can create your test database like so:

```
docker-compose run web createdb -h db -U postgres DATABASE_NAME_test
```

You can lookup the exact name that your test database should be in
`config/test_settings.yml`.

