
FROM node:alpine

LABEL Name="clixplorer"
LABEL Version="2.1"

RUN apk update && apk upgrade && \
    apk add --no-cache git nodejs npm python make g++ bash

WORKDIR /www
RUN git clone https://github.com/Magicking/Clixplorer
WORKDIR Clixplorer
RUN npm install
RUN npm install -g browserify
