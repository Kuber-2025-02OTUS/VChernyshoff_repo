FROM debian:12-slim

ARG NGINX_V=1.26.3



RUN apt-get update && \
    apt-get install -y \
        wget \
        apt-transport-https \
        lsb-release \
        ca-certificates \
        build-essential \
        libpcre3-dev \
        zlib1g-dev && \
    wget http://nginx.org/download/nginx-${NGINX_V}.tar.gz && \
    tar xfz nginx-${NGINX_V}.tar.gz && \
    cd nginx-${NGINX_V} && \
    ./configure --with-http_stub_status_module && \
    make && \
    make install && \
    ln -s /usr/local/nginx/sbin/nginx /usr/bin/nginx

# COPY entrypoint.sh /docker-entrypoint.sh
COPY nginx.conf /usr/local/nginx/conf/nginx.conf


ENTRYPOINT "nginx"
# alpine: gcc g++ zlib-dev linux-headers pcre-dev openssl-dev make 