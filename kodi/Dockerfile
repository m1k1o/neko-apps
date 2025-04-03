ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

#
# install kodi
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends kodi kodi-repository-kodi kodi-pvr-iptvsimple kodi-inputstream-adaptive kodi-inputstream-ffmpegdirect; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

# VOLUME [ "/home/neko/.kodi" ]

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/kodi.conf
