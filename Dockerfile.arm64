FROM ghcr.io/linuxserver/baseimage-ubuntu:arm64v8-focal

ARG DEBIAN_FRONTEND="noninteractive"
ARG RADARR_BRANCH="develop"
ENV XDG_CONFIG_HOME="/config/xdg"

RUN \
 echo "**** install packages ****" && \
 apt-get update && \
 apt-get install --no-install-recommends -y \
	jq \
	libicu66 \
	libmediainfo0v5 \
	sqlite3 && \
 echo "**** install radarr ****" && \
 mkdir -p /app/radarr/bin && \
 curl -o \
	/tmp/radarr.tar.gz -L \
	"$(curl -s "https://api.github.com/repos/nls44/Radarr-AirDCPP/releases/latest" | jq '.assets' | jq -r '.[].browser_download_url | match(".*arm64.tar.gz*";"i") | .string')" && \
 tar ixzf \
	/tmp/radarr.tar.gz -C \
	/app/radarr/bin --strip-components=1 && \
 echo "**** cleanup ****" && \
 rm -rf \
	/app/radarr/bin/Radarr.Update \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*

# copy local files
COPY root/ /

# ports and volumes
EXPOSE 7878
VOLUME /config

