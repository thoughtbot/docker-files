# Haskell Docker Files

This directory contains all the docker files for images
based on the Haskell language.

- [ghc]: An image with the latest GHC version and Cabal installed.
- [yesod]: An image based on GHC that also has `alex`, `happy`, and `yesod-bin`.
- [yesod-bin]: An image based on Yesod that runs the `yesod` command by default.
- [stack]: An image that will build your Heroku application with Stack.

[ghc]: ghc/
[yesod]: yesod/
[yesod-bin]: yesod-bin/
[stack]: stack/
