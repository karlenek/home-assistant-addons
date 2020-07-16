ARG BUILD_FROM=homeassistant/amd64-base:latest
FROM $BUILD_FROM

# TODO: add version as argument

ENV LANG C.UTF-8

WORKDIR /opt

RUN apk add --no-cache unzip
RUN apk add --update nodejs npm dumb-init

ADD https://github.com/karlenek/home-assistant-watcher/archive/v0.1.1.zip /

RUN unzip /v0.1.1.zip -d /opt

RUN mv /opt/home-assistant-watcher-v0.1.1/* /opt/.

RUN npm install

ENTRYPOINT ["dumb-init"]

CMD ["node", "src/index.js"]

LABEL io.hass.version="VERSION" io.hass.type="addon" io.hass.arch="armhf|aarch64|i386|amd64"
