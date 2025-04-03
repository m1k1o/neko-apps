ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL="https://zoom.us/client/latest/zoom_amd64.deb"

#
# install latest zoom
RUN set -eux; apt-get update; \
    wget -O /tmp/zoom.deb "${SRC_URL}"; \
    apt-get install -y --no-install-recommends openbox /tmp/zoom.deb; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/zoom.conf
COPY openbox.xml /etc/neko/openbox.xml
