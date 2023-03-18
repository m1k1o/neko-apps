ARG BASE_IMAGE=m1k1o/neko:base
FROM $BASE_IMAGE

#
# build mpv and jellyfin-media-player
RUN set -eux; apt-get update; \
    apt-get install -y --no-install-recommends openbox pip build-essential autoconf automake libtool libharfbuzz-dev libfreetype6-dev libfontconfig1-dev libx11-dev libxrandr-dev libvdpau-dev libva-dev mesa-common-dev libegl1-mesa-dev yasm libasound2-dev libpulse-dev libuchardet-dev zlib1g-dev libfribidi-dev git libgnutls28-dev libgl1-mesa-dev libsdl2-dev cmake wget python g++ qtwebengine5-dev qtquickcontrols2-5-dev libqt5x11extras5-dev libcec-dev qml-module-qtquick-controls qml-module-qtwebengine qml-module-qtwebchannel qtbase5-private-dev curl unzip; \
    pip install meson; \
    mkdir ~/jmp; cd ~/jmp; \
    git clone --depth 1 --branch mpv-build-rewrite https://github.com/avih/mpv-build.git; \
    cd mpv-build; \
    echo --enable-libmpv-shared > mpv_options; \
    echo --disable-cplayer >> mpv_options; \
    echo --disable-gl >> mpv_options; \
    ./rebuild -j4; \
    ./install; \
    ldconfig; \
    cd ~/jmp/; \
    git clone --depth 1 https://github.com/jellyfin/jellyfin-media-player.git; \
    cd jellyfin-media-player; \
    ./download_webclient.sh; \
    cd build; \
    cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=/usr/local/ ..; \
    make -j4; \
    make install; \
    rm -rf ~/jmp/; \
    #
    # clean up
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/* /tmp/*;

#
# copy configuation files
COPY supervisord.conf /etc/neko/supervisord/jellyfin.conf
COPY openbox.xml /etc/neko/openbox.xml
