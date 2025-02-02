FROM node:22-slim

USER root

ENV LANG=en_US.UTF-8
ENV RUNTIME_UID=10283

RUN apt-get update
RUN apt-get install -y --no-install-recommends \
    fonts-ipafont-gothic \
    fonts-wqy-zenhei \
    fonts-thai-tlwg \
    fonts-khmeros \
    fonts-kacst \
    fonts-freefont-ttf \
    dbus \
    dbus-x11

RUN groupadd -r runtime
RUN useradd -u $RUNTIME_UID -rm -g runtime -G audio,video runtime

ENV DBUS_SESSION_BUS_ADDRESS=autolaunch:
RUN PUPPETEER_CACHE_DIR=/home/runtime/.cache/puppeteer \
  npx puppeteer browsers install chrome --install-deps

RUN apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER runtime
WORKDIR /home/runtime
