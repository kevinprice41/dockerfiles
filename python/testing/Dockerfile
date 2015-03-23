FROM cnry/python:2.7

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    rubygems git-core git make time curl openssh-client build-essential \
    mysql-client \
    libmysqlclient-dev \
    libpq-dev \
    libev-dev \
    libssl-dev \
    libffi-dev \
    mercurial \
    libgraphicsmagick++1-dev \
    libboost-python-dev \
    libxml2-dev \
    libxslt1-dev \
    zip \
    libevent-dev \
  && rm -rf /var/lib/apt/lists/*

RUN \
  mkdir -m 0700 ~/.ssh \
  && ssh-keyscan -t rsa -H github.com > ~/.ssh/known_hosts

RUN gem install fakes3

RUN pip install -U flake8 pip awscli
