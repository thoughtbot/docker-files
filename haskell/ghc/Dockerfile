FROM heroku/cedar:14
MAINTAINER Tony DiPasquale <tony@thoughtbot.com>

# Dependencies
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    bzip2 \
    ca-certificates \
    curl \
    gcc \
    libc6-dev \
    libgmp-dev \
    libgmp10 \
    make \
    patch \
    zlib1g-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# GHC
RUN mkdir -p /usr/src/ghc
WORKDIR /usr/src/ghc

RUN curl --silent -O https://downloads.haskell.org/~ghc/7.10.3/ghc-7.10.3-x86_64-deb8-linux.tar.bz2 \
  && echo '01cfbad8dff1e8b34a5fdca8caeaf843b56e36af919e29cd68870d2588563db5  ghc-7.10.3-x86_64-deb8-linux.tar.bz2' | sha256sum -c - \
  && tar --strip-components=1 -xjf ghc-7.10.3-x86_64-deb8-linux.tar.bz2 \
  && rm ghc-7.10.3-x86_64-deb8-linux.tar.bz2 \
  && ./configure \
  && make install \
  && rm -rf /usr/src/ghc \
  && /usr/local/bin/ghc --version

# Cabal
RUN mkdir -p /usr/src/cabal
WORKDIR /usr/src/cabal

RUN curl --silent -O https://www.haskell.org/cabal/release/cabal-install-1.22.6.0/cabal-install-1.22.6.0.tar.gz \
  && echo '9d239e385696a7faa49f068aea451882baec6a7df26fbddbd08271c9053cb0b4  cabal-install-1.22.6.0.tar.gz' | sha256sum -c - \
  && tar --strip-component=1 -xzf cabal-install-1.22.6.0.tar.gz \
  && rm cabal-install-1.22.6.0.tar.gz \
  && /usr/src/cabal/bootstrap.sh \
  && for pkg in `ghc-pkg --user list  --simple-output`; do ghc-pkg unregister --force $pkg; done \
  && rm -rf /usr/src/cabal \
  && /root/.cabal/bin/cabal --version

WORKDIR /
ENV PATH=/root/.cabal/bin:$PATH
RUN cabal update

CMD ghci

# Done

