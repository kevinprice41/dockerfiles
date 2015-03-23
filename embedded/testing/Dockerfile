FROM cnry/python:2.7

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    build-essential \
    ca-certificates \
    git \
    libcurl4-openssl-dev \
    openssh-client \
    libjansson-dev \
    libssl-dev \
    pkg-config \
    uuid-dev \
    python-dev \
    python-pip \
    wget \
  && rm -rf /var/lib/apt/lists/*

RUN \
  mkdir -m 0700 ~/.ssh \
  && ssh-keyscan -t rsa -H github.com > ~/.ssh/known_hosts

