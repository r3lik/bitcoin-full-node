FROM ubuntu:16.04

LABEL description="Base image for Bitcoin (BTC) fullnode"
LABEL maintainer="mike@r3lik.com"
LABEL version="0.1"

WORKDIR /tmp

RUN apt-get update \
    && apt-get -y --no-install-recommends install ca-certificates curl unzip \
    && curl -L -O https://github.com/electroneum/electroneum/releases/download/v0.11.0.0/linux-x64-0.11.0.0.zip \
    && unzip linux-x64-0.11.0.0.zip \
    && rm linux-x64-0.11.0.0.zip \
    && mv electroneumd /usr/local/bin/electroneumd \
    && chmod a+x /usr/local/bin/electroneumd \
    && rm -r * \
    && apt-get -y remove ca-certificates curl unzip \
    && apt-get -y autoremove \
    && apt-get clean autoclean \
    && rm -rf /var/lib/{apt,dpkg,cache,log}

# blockchain location
VOLUME /root/.electroneum

ENTRYPOINT ["electroneumd"]

# allow connections
CMD ["--restricted-rpc", "--rpc-bind-ip=0.0.0.0", "--confirm-external-bind"]
