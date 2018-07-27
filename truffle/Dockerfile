FROM node:alpine

MAINTAINER Nelson Herbin <nelson@herbin.info>

LABEL name=truffle
LABEL version=1

RUN apk update && apk upgrade && apk add -t .gyp --no-cache git python g++ make bash nodejs npm
RUN npm install -g truffle
WORKDIR truffle
RUN truffle unbox webpack
COPY . .