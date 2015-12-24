FROM thoughtbot/ghc:7.10.3
MAINTAINER Tony DiPasquale <tony@thoughtbot.com>

# Install postgres client
RUN apt-get update
RUN apt-get install -y postgresql-client

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

