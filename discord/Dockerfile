ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL="https://discordapp.com/api/download?platform=linux&format=deb"

#
# install latest discord and required libraries
RUN set -eux; apt-get update; \
    wget -O /tmp/discord.deb "${SRC_URL}"; \
    apt-get install -y --no-install-recommends libatk1.0-0 libatk-bridge2.0-0 libgtk-3-0 openbox /tmp/discord.deb; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/discord.conf
COPY openbox.xml /etc/neko/openbox.xml
