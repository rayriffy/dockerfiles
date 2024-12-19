FROM myoung34/github-runner:debian-bookworm

# chromium
RUN apt-get install --no-install-recommends --yes chromium

# nodejs
RUN curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - && \
  apt-get install --no-install-recommends --yes nodejs && \
  npm i --location=global pnpm

# cleanup
RUN rm -rf /var/lib/apt/lists/* && \
  apt-get clean
