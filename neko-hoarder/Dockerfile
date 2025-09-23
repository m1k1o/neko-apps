ARG BASE_IMAGE=ghcr.io/m1k1o/neko/base:latest
FROM $BASE_IMAGE

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends curl gnupg openbox socat xdotool scrot; \
    curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg; \
    echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main" | tee /etc/apt/sources.list.d/brave-browser-release.list; \
    apt-get update; \
    apt-get install -y --no-install-recommends openbox socat xdotool scrot brave-browser; \
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*