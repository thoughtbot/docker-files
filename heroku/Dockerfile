FROM ubuntu

RUN apt-get update
RUN apt-get install -y jq wget
RUN wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh

WORKDIR /
COPY upload-slug.sh ./

CMD /bin/bash

