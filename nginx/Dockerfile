FROM nginx:alpine

RUN apk add bash
#ADD nginx.conf /etc/nginx/nginx.conf

#RUN echo "server {\
#  listen 443 ssl; \
#  ssl on;\
#  ssl_certificate     /opt/ssl/server.crt;\
#  ssl_certificate_key /opt/ssl/server.key;\
#  ssl_session_timeout 5m; \
#  ssl_session_cache shared:SSL:10m; \
#  ssl_protocols TLSv1 TLSv1.1 TLSv1.2; \
#  ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH'; \
#  ssl_prefer_server_ciphers on; \
#  server_name localhost; \
#  location / { \
#    root   /usr/share/nginx/html; \
#    index  index.html index.htm; \
#  }\
#  error_page   500 502 503 504  /50x.html;\
#  location = /50x.html {\
#    root   /usr/share/nginx/html;\
#  }\
#}" > /etc/nginx/conf.d/ssl.conf

#COPY --from=builder  /server.crt /opt/ssl/server.crt
#COPY --from=builder  /server.key /opt/ssl/server.key


EXPOSE 80