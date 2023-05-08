FROM nginxinc/nginx-unprivileged:1.24-alpine3.17 as base
# https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
USER root
RUN echo "************" && find /usr/share -name "zoneinfo"
RUN mkdir -p /opt/var/cache/nginx && \
    cp -a --parents /usr/lib/nginx /opt && \
    cp -a --parents /usr/share/nginx /opt && \
    cp -a --parents /var/log/nginx /opt && \
    cp -aL --parents /var/run /opt && \
    cp -a --parents /etc/nginx /opt && \
    cp -a --parents /etc/passwd /opt && \
    cp -a --parents /etc/group /opt && \
    cp -a --parents /usr/sbin/nginx /opt && \
    cp -a --parents /usr/sbin/nginx-debug /opt && \
    cp -a --parents /lib/libcrypto.so.* /opt && \
    cp -a --parents /lib/libz.* /opt && \
    cp -a --parents /lib/libc.* /opt && \
    cp -a --parents /lib/ld-musl* /opt && \
    cp -a --parents /lib/libssl.so.* /opt && \
    cp -a --parents /usr/lib/lib* /opt && \
    cp /usr/share/zoneinfo/Asia/Tokyo /opt/etc/localtime

FROM gcr.io/distroless/base-debian11 as runtime
COPY --from=base /opt /
EXPOSE 8080
STOPSIGNAL SIGTERM
USER 1001
ENTRYPOINT ["nginx", "-g", "daemon off;"]
