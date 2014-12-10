FROM debian:jessie

MAINTAINER devops@canary.is

ENV DEBIAN_FRONTEND noninteractive
ENV FAKE_S3_ROOT    /srv/fake-s3

RUN mkdir -p "$FAKE_S3_ROOT" && chown daemon:daemon "$FAKE_S3_ROOT"

WORKDIR $FAKE_S3_ROOT

RUN apt-get update \
  && apt-get -y install ruby rubygems-integration git \
  && rm -rf /var/lib/apt/lists/*

ENV FAKES3_VERSION 0.1.6.1
ENV FAKES3_BRANCH missing-content-type
ENV FAKES3_REPO https://github.com/bison/fake-s3.git

RUN git clone --branch $FAKES3_BRANCH $FAKES3_REPO /tmp/fake-s3 \
  && cd /tmp/fake-s3 \
  && gem build fakes3.gemspec \
  && gem install ./fakes3-$FAKES3_VERSION.gem

EXPOSE 8080

VOLUME [$FAKE_S3_ROOT]

USER daemon

CMD exec fakes3 server --port=8080 --root="$FAKE_S3_ROOT"
