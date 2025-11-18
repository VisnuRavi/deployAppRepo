FROM node:25-alpine3.21 as build-stage

RUN npm install -g @angular/cli

WORKDIR /app

COPY angular.json .
COPY package.json .
COPY package-lock.json .
COPY tsconfig.app.json .
COPY tsconfig.json . 
COPY tsconfig.spec.json .
COPY public public
COPY src src

RUN npm ci

RUN ng build

FROM caddy:2.10.2-alpine as prod-stage

WORKDIR caddy

COPY caddy/Caddyfile .

RUN mkdir html

COPY --from=build-stage app/dist/angular/browser/ ./html
COPY caddy/error.html ./html

ENV CADDY_PORT=3000

EXPOSE ${CADDY_PORT}

ENTRYPOINT caddy run --config Caddyfile