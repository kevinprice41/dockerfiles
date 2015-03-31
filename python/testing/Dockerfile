FROM debian:jessie

ENV DEBIAN_FRONTEND  noninteractive
ENV PYTHONUNBUFFERED true
ENV VIRTUAL_ENV      /usr/local/virtualenv
ENV PATH             $VIRTUAL_ENV/bin:$PATH

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    rubygems \
    git \
    make \
    time \
    curl \
    openssh-client \
    build-essential \
    gcc \
    g++ \
    libc6-dev \
    python2.7 \
    python2.7-dev \
    python-pip \
    mysql-client \
    libmysqlclient-dev \
    libpq-dev \
    unzip \
    libev-dev \
    libldap2-dev \
    libsasl2-dev \
    libssl-dev \
    libffi-dev \
    mercurial \
    libgraphicsmagick++1-dev \
    libboost-python-dev \
    libxml2-dev \
    libxslt1-dev \
    zip \
    libevent-dev \
    libev-dev \
  && rm -rf /var/lib/apt/lists/*

RUN \
  mkdir -m 0700 ~/.ssh \
  && ssh-keyscan -t rsa -H github.com > ~/.ssh/known_hosts

RUN gem install fakes3

RUN pip install -U flake8 pip awscli

RUN pip install virtualenv \
  && mkdir -p "${VIRTUAL_ENV}" \
  && virtualenv "${VIRTUAL_ENV}"
