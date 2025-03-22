ARG BASE_IMAGE=m1k1o/neko:base
FROM $BASE_IMAGE

#
# install vlc
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends openbox qbittorrent; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

ENV NEKO_FILE_TRANSFER_ENABLED="true"

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/vlc.conf
COPY openbox.xml /etc/neko/openbox.xml
