FROM alpine

EXPOSE 443
 
#nginx SSL
RUN apk update && apk upgrade && apk add --no-cache \
    nginx \ 
    openssl 

RUN mkdir -p /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
    -out /etc/nginx/ssl/ddalee42.duckdns.org.crt \
    -keyout /etc/nginx/ssl/ddalee42.duckdns.org.key \
    -subj "/C=Fr/ST=IledeFrance/L=Paris/O=42 School/CN=ddalee42.duckdns.org"

#nginx config
RUN mkdir -p /run/nginx
COPY conf/nginx.conf /etc/nginx/http.d/default.conf

ENTRYPOINT ["nginx", "-g", "daemon off;"]
