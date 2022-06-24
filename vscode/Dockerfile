ARG BASE_IMAGE=m1k1o/neko:base
FROM $BASE_IMAGE

ARG SRC_URL="https://go.microsoft.com/fwlink/?LinkID=760868"

#
# install latest vscode
RUN set -eux; apt-get update; \
    wget -O /tmp/vscode.deb "${SRC_URL}"; \
    apt-get install -y --no-install-recommends openbox /tmp/vscode.deb; \
    apt-get install -f; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/firefox.conf
COPY openbox.xml /etc/neko/openbox.xml
