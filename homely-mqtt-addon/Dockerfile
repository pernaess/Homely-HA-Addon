ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base:3.19
FROM ${BUILD_FROM}

# Installer Node.js 18 + npm + byggverktøy
RUN apk add --no-cache nodejs npm python3 make g++

# Sett arbeidsmappe
WORKDIR /app

# Kopier app-kode
COPY rootfs/app /app

# Installer dependencies og bygg TypeScript
RUN npm install
RUN npm run build
RUN npm prune --production

# Kopier run-script
COPY run.sh /
RUN chmod a+x /run.sh

# Start add-on
CMD ["/run.sh"]
