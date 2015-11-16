FROM alpine:3.2

ENV ARCHIVE https://github.com/couchbase/couchbase-cli/archive
ENV TAG 2.5.1
ENV HOME /home/couchbase

RUN mkdir -p $HOME
WORKDIR $HOME

RUN apk update \
    && apk add --virtual build-dependencies ca-certificates wget unzip \
    && apk add python \
    && wget $ARCHIVE/$TAG.zip -O $HOME/$TAG.zip \
    && unzip $HOME/$TAG.zip -d $HOME \
    && mv $HOME/couchbase-cli-$TAG couchbase-cli \
    && rm -rf $HOME/$TAG.zip \
    && rm -rf /var/cache/apk/* \
    && apk del build-dependencies

ENTRYPOINT ["couchbase-cli/couchbase-cli"]
