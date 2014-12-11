FROM cnry/python:2.7

ENV MOCK_S3_ROOT /srv/mock-s3

RUN mkdir -p "$MOCK_S3_ROOT" && chown daemon:daemon "$MOCK_S3_ROOT"

WORKDIR $MOCK_S3_ROOT

RUN apt-get update \
  && apt-get -y install git \
  && rm -rf /var/lib/apt/lists/*

ENV MOCK_S3_REPO https://github.com/jserver/mock-s3.git

RUN git clone $MOCK_S3_REPO /tmp/mock-s3 \
  && cd /tmp/mock-s3 \
  && python setup.py install

ENV MOCK_S3_PORT 8080

VOLUME [$MOCK_S3_ROOT]

USER daemon

CMD exec mock_s3 --host 0.0.0.0 --port $MOCK_S3_PORT --root $MOCK_S3_ROOT
