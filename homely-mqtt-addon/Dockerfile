ARG BUILD_FROM
FROM ${BUILD_FROM}

RUN apk add --no-cache python3 make g++

WORKDIR /app

COPY rootfs/app /app

RUN npm install
RUN npm run build
RUN npm prune --production

COPY run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
