FROM alpine AS builder

ENV VIPS_VERSION 8.18.2

WORKDIR /libvips

RUN wget -O- https://github.com/libvips/libvips/releases/download/v$VIPS_VERSION/vips-$VIPS_VERSION.tar.xz | tar xJC /libvips
RUN apk update && \
    apk add --no-cache zlib libxml2 glib gobject-introspection libjpeg-turbo libexif lcms2 fftw cgif libpng libwebp libwebpmux libwebpdemux highway tiff poppler-glib \
    librsvg libarchive openexr-libopenexr libheif libimagequant libjxl pango build-base meson ninja zlib-dev libxml2-dev glib-dev gobject-introspection-dev \
    libjpeg-turbo-dev libexif-dev lcms2-dev fftw-dev cgif-dev libpng-dev libwebp-dev highway-dev tiff-dev poppler-dev librsvg-dev libarchive-dev openexr-dev \
    libheif-dev libimagequant-dev libjxl-dev pango-dev py-gobject3-dev

RUN cd vips-$VIPS_VERSION && \
    meson setup build --prefix /usr/local -Dmagick=disabled && \
    cd build && \
    meson compile && \
    meson test && \
    DESTDIR=/opt/vips meson install

FROM alpine AS runner

COPY --from=builder /opt/vips /opt/vips
RUN ldconfig
