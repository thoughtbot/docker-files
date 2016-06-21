FROM heroku/cedar:14
MAINTAINER Joe Ferris <jferris@thoughtbot.com>
ENV LANG en_US.UTF-8

RUN mkdir /deb
RUN cd /deb \
  && wget --quiet \
  https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb \
  && dpkg -i erlang-solutions_1.0_all.deb

RUN apt-get update && \
  apt-get install -y --no-install-recommends \
  erlang \
  erlang-dev \
  erlang-doc \
  erlang-src

RUN mkdir /build
RUN cd /build \
  && wget --quiet \
  https://github.com/elixir-lang/elixir/archive/v1.3.0.tar.gz \
  && echo "66cb8448dd60397cad11ba554c2613f732192c9026468cff55e8347a5ae4004a v1.3.0.tar.gz" \
  | sha256sum -c - \
  && tar -xf v1.3.0.tar.gz \
  && cd elixir-1.3.0 \
  && make install

CMD iex
