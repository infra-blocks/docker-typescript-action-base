ARG NODE_VERSION

FROM node:${NODE_VERSION}-alpine
ONBUILD COPY tsconfig.json tsconfig.build.json package.json package-lock.json /action/
ONBUILD COPY src /action/src
ONBUILD RUN cd /action/ && \
    npm ci && \
    npm run build && \
    npm prune --production && \
    rm -rf src tsconfig.json tsconfig.build.json

ENTRYPOINT ["node", "--enable-source-maps", "/action/dist/index.js"]
