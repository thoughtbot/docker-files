FROM thoughtbot/ghc:7.10.1
MAINTAINER Tony DiPasquale <tony@thoughtbot.com>

# Install cabal dependencies
RUN cabal update
RUN cabal install alex
RUN cabal install happy
RUN cabal install yesod-bin
RUN export PATH=/root/.cabal/bin:$PATH
#
# Done
WORKDIR /

