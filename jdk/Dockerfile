FROM debian:jessie

ENV DEBIAN_FRONTEND  noninteractive

MAINTAINER devops@canary.is

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    openjdk-7-jdk \
  && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
