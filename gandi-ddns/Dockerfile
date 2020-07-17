ARG BUILD_FROM=homeassistant/amd64-base:latest
FROM $BUILD_FROM

ARG GANID_DDNS_VERSION

ENV LANG C.UTF-8

WORKDIR /opt

RUN apk add --no-cache unzip
RUN apk add --update nodejs npm dumb-init

RUN wget --quiet -O /tmp/repo.zip "https://github.com/karlenek/gandi-ddns/archive/v${GANID_DDNS_VERSION}.zip" && \
    unzip /tmp/repo.zip -d /opt && \
    mv /opt/gandi-ddns-${GANID_DDNS_VERSION}/* /opt/.

RUN npm install

ENTRYPOINT ["dumb-init"]

CMD ["node", "src/index.js"]

LABEL io.hass.version="VERSION" io.hass.type="addon" io.hass.arch="armhf|aarch64|i386|amd64"
