ARG BASE_IMAGE=m1k1o/neko:base
FROM $BASE_IMAGE

#
# install kodi
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends kodi; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/kodi.conf
