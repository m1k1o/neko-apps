ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

#
# install latest obs
RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends openbox obs-studio ffmpeg; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/obs.conf
COPY openbox.xml /etc/neko/openbox.xml
