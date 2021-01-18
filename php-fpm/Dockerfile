FROM php:7-fpm-alpine

RUN sed -i "s@http://dl-cdn.alpinelinux.org/@https://mirrors.huaweicloud.com/@g" /etc/apk/repositories && \
  apk update && apk add wget make \
  && apk add freetype-dev jpeg-dev autoconf gcc g++ \
  && apk add libzip-dev \
  && apk add libsodium-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-configure zip \
  && docker-php-ext-configure sodium \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-install -j$(nproc) zip \
  && docker-php-ext-install -j$(nproc) sodium \
  && docker-php-ext-install -j$(nproc) bcmath pdo_mysql \
  && pecl install redis \
  && pecl install mongodb \
  && docker-php-ext-enable redis bcmath pdo_mysql mongodb \
  && rm -rf /var/cache/apk/*