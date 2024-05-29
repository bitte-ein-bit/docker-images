FROM debian:bookworm-slim

RUN apt-get update && \
    apt-get install wget python3-pip -y && \
    mkdir -p /etc/apt/keyrings && \
    wget -q -O /etc/apt/keyrings/mopidy-archive-keyring.gpg https://apt.mopidy.com/mopidy.gpg && \
    wget -q -O /etc/apt/sources.list.d/mopidy.list https://apt.mopidy.com/bullseye.list && \
    apt-get update && \
    apt-get install mopidy -y && \
    apt-get clean && \
    python3 -m pip install Mopidy-Subidy Mopidy-Iris --break-system-packages && \
    rm -rf /var/lib/apt/lists/* /root/.cache/* /tmp/*
CMD [ "mopidy" ]