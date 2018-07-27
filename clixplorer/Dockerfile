
FROM node:alpine
LABEL Name="clixplorer"
LABEL Version="2.1"

RUN apk update && apk upgrade && \
    apk add --no-cache git nodejs npm python make g++ nginx bash

RUN git clone https://github.com/Magicking/Clixplorer
WORKDIR Clixplorer

RUN npm install
RUN npm install -g browserify

FROM nginx:alpine

ADD nginx.conf /etc/nginx/nginx.conf
COPY . /usr/share/nginx/html
EXPOSE 8080
EXPOSE 80