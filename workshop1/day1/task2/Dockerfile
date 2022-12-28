FROM node:19.3

WORKDIR /app

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD views views
ADD public public

RUN npm ci

ENV APP_PORT=3000
EXPOSE 3000
ENV INSTANCE_NAME=""
ENV INSTANCE_HASH=""

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
	CMD curl -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT node main.js
