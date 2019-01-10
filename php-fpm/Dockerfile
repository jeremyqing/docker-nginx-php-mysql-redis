FROM alpine:3.8

MAINTAINER jeremy yao <437746288@qq.com>

RUN echo "http://mirrors.ustc.edu.cn/alpine/v3.8/main" > /etc/apk/repositories \
    && echo "http://mirrors.ustc.edu.cn/alpine/v3.8/community" >> /etc/apk/repositories

ENV TIMEZONE Asia/Shanghai

RUN apk update && \
  apk add --no-cache tzdata && \
  cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
  echo "${TIMEZONE}" > /etc/timezone && \
  apk add php7-curl \
    php7-bcmath \
    php7-bz2 \
    php7-ctype \
    php7-dev \
    php7-dom \
    php7-event \
    php7-exif \
    php7-fileinfo \
    php7-fpm \
    php7-gd \
    php7-gmp \
    php7-gettext \
    php7-gmp \
    php7-gmagick \
    php7-intl \
    php7-iconv \
    php7-imagick \
    php7-imagick-dev \
    php7-json \
    php7-mbstring \
    php7-mcrypt \
    php7-mysqli \
    php7-mysqlnd \
    php7-memcached \
    php7-mongodb \
    php7-sysvmsg \
    php7-sysvsem \
    php7-sysvshm \
    php7-session \
    php7-ssh2 \
    php7-openssl \
    php7-opcache \
    php7-pdo \
    php7-pdo_mysql \
    php7-pdo_sqlite \
    php7-phar \
    php7-pcntl \
    php7-posix \
    php7-redis \
    php7-simplexml \
    php7-xsl \
    php7-tokenizer \
    php7-xml \
    php7-xmlreader \
    php7-xmlrpc \
    php7-xmlwriter \
    php7-zip \
    php7-zlib \
    php7 \
    openssh-client &&\
  rm -rf /var/cache/apk/*

RUN set -x \
  && addgroup -g 82 -S www-data \
  && mkdir -p /var/www/html \
  && adduser -u 82 -D -s /sbin/nologin -h /var/www/html -G www-data www-data
RUN mkdir /var/log/php \
  && chown -R www-data:www-data /var/log/php \
  && chmod -R 754 /var/log/php

EXPOSE 9000
CMD ["/usr/sbin/php-fpm7", "-F"]
