FROM php:7.3-fpm-alpine

RUN apk update \
    && apk add --no-cache tzdata git curl nginx composer \
    && docker-php-ext-install pdo pdo_mysql \
    # timezone
    && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    # php-fpm
    && mkdir -p /var/run/php-fpm && chown www-data:www-data /var/run/php-fpm \
    && rm -f /usr/local/etc/php-fpm.d/zz-docker.conf \
    # nginx
    && mkdir -p /run/nginx \
    # clean up
    && rm -rf /var/cache/apk/*
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY ./nginx/conf.d /etc/nginx/conf.d
COPY ./php-fpm/php-fpm.d/www.conf /usr/local/etc/php-fpm.d/www.conf
