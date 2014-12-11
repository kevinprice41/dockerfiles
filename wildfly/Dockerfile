FROM cnry/jdk

RUN adduser --quiet --system --uid 1000 --group --disabled-login \
  --home /srv/jboss jboss

WORKDIR /srv/jboss

RUN apt-get update \
  && apt-get --yes --no-install-recommends install \
    curl \
    unzip \
  && rm -rf /var/lib/apt/lists/*

USER jboss

ENV WILDFLY_VERSION 8.2.0.Final
ENV WILDFLY_URL http://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz

RUN curl "$WILDFLY_URL" | tar zx && mv wildfly-$WILDFLY_VERSION wildfly

ENV DEPLOYMENTS_DIR /srv/jboss/wildfly/standalone/deployments

EXPOSE 8080 9990

CMD exec /srv/jboss/wildfly/bin/standalone.sh -b 0.0.0.0 $WILDFLY_OPTS
