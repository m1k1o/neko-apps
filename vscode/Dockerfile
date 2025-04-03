ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL="https://go.microsoft.com/fwlink/?LinkID=760868"

#
# install latest vscode
RUN set -eux; apt-get update; \
    wget -O /tmp/vscode.deb "${SRC_URL}"; \
    apt-get install -y --no-install-recommends gnupg openbox /tmp/vscode.deb; \
    apt-get install -f; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/vscode.conf
COPY openbox.xml /etc/neko/openbox.xml
