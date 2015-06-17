FROM thoughtbot/ghc:7.10.1-1
MAINTAINER Tony DiPasquale <tony@thoughtbot.com>

# Install cabal dependencies
RUN mkdir -p /opt/tools
WORKDIR /opt/tools

RUN cabal sandbox init
RUN cabal install alex
RUN cabal install happy
RUN cabal install yesod-bin

ENV PATH /opt/tools/.cabal-sandbox/bin:$PATH

WORKDIR /

# Done

