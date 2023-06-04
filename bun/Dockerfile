FROM debian:11.6-slim AS packager

WORKDIR /app

RUN apt update
RUN apt install curl unzip -y
RUN curl https://bun.sh/install | bash


FROM gcr.io/distroless/base-debian11 as runtime

WORKDIR /app
COPY --from=packager /root/.bun/bin/bun bun

ENTRYPOINT ["./bun"]
