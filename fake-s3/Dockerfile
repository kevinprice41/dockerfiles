FROM debian:jessie

MAINTAINER devops@canary.is

ENV DEBIAN_FRONTEND noninteractive
ENV FAKE_S3_ROOT    /srv/fake-s3

RUN mkdir -p "$FAKE_S3_ROOT" && chown daemon:daemon "$FAKE_S3_ROOT"

WORKDIR $FAKE_S3_ROOT

RUN apt-get update && \
  apt-get -y install ruby rubygems-integration && \
  rm -rf /var/lib/apt/lists/*

RUN gem install fakes3 -v 0.1.6.1

EXPOSE 8080

VOLUME [$FAKE_S3_ROOT]

USER daemon

CMD exec fakes3 server --port=8080 --root="$FAKE_S3_ROOT"
