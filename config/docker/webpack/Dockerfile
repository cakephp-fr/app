FROM node:9.9

MAINTAINER cake17 <cake17@cake-websites.com>

RUN mkdir -p /front

RUN npm install webpack -g

WORKDIR /front
COPY ./ ./front

RUN npm install

EXPOSE 8080

CMD npm run serve
