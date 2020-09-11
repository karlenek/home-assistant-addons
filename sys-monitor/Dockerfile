ARG BUILD_FROM=homeassistant/amd64-base:latest
FROM $BUILD_FROM

ARG SYSM_VERSION=0.0.1

ENV LANG C.UTF-8

WORKDIR /opt

RUN apk add --no-cache unzip
RUN apk add --update nodejs npm dumb-init

RUN wget --quiet -O /tmp/repo.zip "https://github.com/karlenek/sys-monitor/archive/v${SYSM_VERSION}.zip" && \
    unzip /tmp/repo.zip -d /opt && \
    mv /opt/sys-monitor-${SYSM_VERSION}/* /opt/.

RUN npm install

ENTRYPOINT ["dumb-init"]

CMD ["node", "src/index.js"]

LABEL io.hass.version="VERSION" io.hass.type="addon" io.hass.arch="armhf|aarch64|i386|amd64"
