ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL_APP="https://www.stremio.com/downloads"
ARG SRC_URL_ACC1="http://mirrors.kernel.org/ubuntu/pool/multiverse/f/fdk-aac/"
ARG SRC_URL_ACC2="https://www.deb-multimedia.org/pool/main/f/fdk-aac-dmo/"

#
# install latest stremio and required libraries
RUN set -eux; apt-get update; \
    wget -O /tmp/stremio.deb "$(curl -L -s ${SRC_URL_APP} | sed -nE 's#.*(https://dl.strem.io/shell-linux/v[0-9]+.[0-9]+.[0-9]+/stremio_[0-9]+.[0-9]+.[0-9]+-.*amd64.deb).*#\1\n#p')"; \
    wget -O /tmp/libfdk-aac1.deb "$(curl -L -s ${SRC_URL_ACC1} | sed -nE "s#^.*(libfdk-aac1.*amd64.deb).*#$SRC_URL_ACC1\1#p" | sed '$!d')"; \
    wget -O /tmp/libfdk-aac2.deb "$(curl -L -s ${SRC_URL_ACC2} | sed -nE "s#^.*(libfdk-aac2.*dmo2.*amd64.deb).*#$SRC_URL_ACC2\1#p" | sed '$!d')"; \
    apt-get install -y --no-install-recommends /tmp/libfdk-aac1.deb /tmp/libfdk-aac2.deb xdg-utils openbox /tmp/stremio.deb; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/stremio.conf
COPY openbox.xml /etc/neko/openbox.xml
