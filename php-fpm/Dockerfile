FROM php:7-fpm-alpine3.12

RUN \
  sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories  && \
  apk update && apk add wget make icu-dev \
  && apk add ca-certificates freetype-dev jpeg-dev autoconf gcc g++ openssl-dev curl-dev mongo-c-driver-static mongo-c-driver openssl-dev \
  && apk add libzip-dev \
  && apk add libsodium-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-configure zip \
  && docker-php-ext-configure sodium \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-install -j$(nproc) zip \
  && docker-php-ext-install -j$(nproc) sodium \
  && docker-php-ext-install -j$(nproc) bcmath pdo_mysql intl
  && pecl channel-update pecl.php.net \
  && pecl install redis \
  && pecl install mongodb \
  && docker-php-ext-enable redis bcmath pdo_mysql mongodb intl \
  && rm -rf /var/cache/apk/*