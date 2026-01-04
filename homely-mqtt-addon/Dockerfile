ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base-node18:3.19
FROM ${BUILD_FROM}

# Installer byggverktøy
RUN apk add --no-cache python3 make g++

WORKDIR /app

# Kopier appen
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
