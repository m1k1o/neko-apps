ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

#
# install stremio
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends xdg-utils openbox gnupg2; \
    wget -qO - https://debian.vejeta.com/key.gpg | gpg --dearmor -o /usr/share/keyrings/stremio-debian.gpg; \
    echo "deb [signed-by=/usr/share/keyrings/stremio-debian.gpg] https://debian.vejeta.com trixie main non-free" | tee /etc/apt/sources.list.d/stremio.list; \
    apt-get update -y; \
    apt-get install -y --no-install-recommends stremio stremio-server; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/stremio.conf
COPY openbox.xml /etc/neko/openbox.xml
