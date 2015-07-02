# GHC Docker Image

A base image with the latest GHC and Cabal installed.

## Usage

You can start writing Haskell by starting the container.

```
docker run --rm -it thoughtbot/ghc
```

This will start the container and run `ghci`.

You can also create your own `Dockerfile`s inheriting from this image.

```
FROM thoughtbot/ghc
```

