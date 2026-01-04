ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base:3.19
FROM ${BUILD_FROM}

# Installer Node.js 18 og npm
RUN apk add --no-cache nodejs npm python3 make g++

WORKDIR /app
COPY rootfs/app /app

RUN npm install
RUN npm run build
RUN npm prune --production

COPY run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
