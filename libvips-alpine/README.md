## libvips-alpine

pre-built libvips ready-to-copy over to any project

```Dockerfile
FROM ghcr.io/rayriffy/libvips-alpine:latest AS libvips

FROM alpine AS runner
COPY --from=libvips /opt/vips/usr/local /usr/local
RUN ldconfig
```
