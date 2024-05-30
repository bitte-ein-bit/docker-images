FROM python:3.12-alpine3.20

# renovate: datasource=repology depName=alpine_3_20/snapcast versioning=loose
ARG SNAPCAST_VERSION=0.28.0-r1
# renovate: datasource=github-releases depName=badaix/snapweb
ARG SNAPWEB_VERSION=v0.7.0

RUN apk add --no-cache \
    bash \
    snapcast-server=${SNAPCAST_VERSION} \
    wget \
    sed \
    # Python dependencies
    python3 \
    py3-pip \
    pkgconfig \
    py3-gobject3 && \
    # For snapweb
    wget -O /tmp/snapweb.zip https://github.com/badaix/snapweb/releases/download/${SNAPWEB_VERSION}/snapweb.zip && \
    cd /usr/share/snapserver/snapweb && \
    rm -rf * && \
    unzip /tmp/snapweb.zip && \
    rm /tmp/snapweb.zip && \
    # Install python dependencies for control scripts
    python3 -m pip install \
    python-mpd2 \
    musicbrainzngs \
    websocket-client

EXPOSE 1704
EXPOSE 1780

ENTRYPOINT ["snapserver"]