FROM cnry/python:2.7

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    rubygems git-core openssh-client build-essential \
    libmysqlclient-dev \
    libpq-dev \
    libev-dev \
    libssl-dev \
    libffi-dev \
    libevent-dev
  && rm -rf /var/lib/apt/lists/*

RUN \
  mkdir -m 0700 ~/.ssh \
  && ssh-keyscan -t rsa -H github.com > ~/.ssh/known_hosts

RUN gem install fakes3

RUN pip install -U flake8 pip awscli
