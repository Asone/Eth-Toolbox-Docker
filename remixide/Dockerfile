FROM alpine:3.8

MAINTAINER Nelson Herbin <nelson@herbin.info>

RUN apk update && apk upgrade && \
    apk add --no-cache git nodejs npm python make g++   


RUN git clone https://github.com/ethereum/remix-ide.git
WORKDIR "/remix-ide/"

RUN npm install
RUN npm run setupremix  # this will clone https://github.com/ethereum/remix for you and link it to remix-ide