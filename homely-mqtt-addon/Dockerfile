ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.19
FROM ${BUILD_FROM}

# Install Node.js 18 LTS and dependencies
RUN apk add --no-cache nodejs18 npm python3 make g++

WORKDIR /app

# Copy the entire application
COPY rootfs/app /app

# Install dependencies
RUN npm install
RUN npm install js-yaml

# Build TypeScript
RUN npm run build

# Remove devDependencies
RUN npm prune --production

# Copy our add-on run script
COPY run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
