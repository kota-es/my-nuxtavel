FROM node:lts-alpine3.11

WORKDIR /var/www

RUN apk update && \
    apk add git && \
    npm install -g npm && \
    npm install -g vue-cli && \
    npm install -g create-nuxt-app@2.15.0

ENV HOST 0.0.0.0
EXPOSE 3000