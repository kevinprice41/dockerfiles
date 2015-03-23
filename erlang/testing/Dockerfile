FROM debian:jessie

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    build-essential \
    time \
    mercurial \
    erlang-dev \
    erlang-src \
    erlang-nox \
    xsltproc \
    zip \
    netcat \
    ant \
  && rm -rf /var/lib/apt/lists/*

RUN \
  mkdir -m 0700 ~/.ssh \
  && ssh-keyscan -t rsa -H github.com > ~/.ssh/known_hosts
