# Base image med Node 18 (for ARM64)
ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base-node18:3.19
FROM ${BUILD_FROM}

# Installer nødvendige pakker for bygging
RUN apk add --no-cache python3 make g++

# Sett arbeidsmappe
WORKDIR /app

# Kopier applikasjonen inn
COPY rootfs/app /app

# Installer npm-dependencies
RUN npm install
RUN npm install js-yaml

# Bygg TypeScript
RUN npm run build

# Fjern devDependencies, behold produksjonsdependencies
RUN npm prune --production

# Kopier run-script
COPY run.sh /
RUN chmod a+x /run.sh

# Start add-on
CMD ["/run.sh"]
