ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base-node18:3.19
FROM ${BUILD_FROM}

# Installer kun bygg-verktøy
RUN apk add --no-cache python3 make g++

WORKDIR /app
COPY rootfs/app /app

# Installer alt fra package.json (dev + prod)
RUN npm install

# Bygg TypeScript
RUN npm run build

# Fjern devDependencies
RUN npm prune --production

COPY run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
