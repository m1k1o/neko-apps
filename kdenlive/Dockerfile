ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

#
# install kdenlive
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends openbox kdenlive frei0r-plugins breeze-icon-theme; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/kdenlive.conf
COPY openbox.xml /etc/neko/openbox.xml
