ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL="https://dl.strem.io/shell-linux/v4.4.168/stremio_4.4.168-1_amd64.deb"
ARG SRC_URL_LIBFDK_ACC1="http://mirrors.kernel.org/ubuntu/pool/multiverse/f/fdk-aac/libfdk-aac1_0.1.6-1_amd64.deb"
ARG SRC_URL_LIBFDK_ACC2="https://www.deb-multimedia.org/pool/main/f/fdk-aac-dmo/libfdk-aac2_2.0.2-dmo2_amd64.deb"

#
# install latest stremio and required libraries
RUN set -eux; apt-get update; \
    wget -O /tmp/libfdk-aac1.deb "${SRC_URL_LIBFDK_ACC1}"; \
    wget -O /tmp/libfdk-aac2.deb "${SRC_URL_LIBFDK_ACC2}"; \
    wget -O /tmp/stremio.deb "${SRC_URL}"; \
    apt-get install -y --no-install-recommends /tmp/libfdk-aac1.deb /tmp/libfdk-aac2.deb xdg-utils openbox /tmp/stremio.deb; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/stremio.conf
COPY openbox.xml /etc/neko/openbox.xml
