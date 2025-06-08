ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

ARG SRC_URL="https://downloader.cursor.com/linux/appImage/x64"

#
# install latest cursor and required dependencies
RUN set -eux; apt-get update; \
    # Install dependencies for Cursor (Electron app)
    apt-get install -y --no-install-recommends \
        wget \
        curl \
        libgtk-3-0 \
        libgconf-2-4 \
        libnss3 \
        libxss1 \
        libasound2 \
        libxtst6 \
        libatspi2.0-0 \
        libdrm2 \
        libxcomposite1 \
        libxdamage1 \
        libxrandr2 \
        libgbm1 \
        libcups2 \
        openbox; \
    # Download and install Cursor
    wget -O /tmp/cursor.AppImage "${SRC_URL}"; \
    chmod +x /tmp/cursor.AppImage; \
    cd /tmp && ./cursor.AppImage --appimage-extract; \
    mv squashfs-root /opt/cursor; \
    # Create executable wrapper that handles Electron flags
    echo '#!/bin/bash' > /usr/bin/cursor; \
    echo 'exec /opt/cursor/AppRun --no-sandbox --disable-gpu-sandbox "$@"' >> /usr/bin/cursor; \
    chmod +x /usr/bin/cursor; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuration files
COPY supervisord.conf /etc/neko/supervisord/cursor.conf
COPY openbox.xml /etc/neko/openbox.xml 