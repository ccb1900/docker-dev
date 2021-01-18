# FROM composer:1
FROM php:7-alpine
RUN sed -i "s@http://dl-cdn.alpinelinux.org/@https://mirrors.huaweicloud.com/@g" /etc/apk/repositories && \
apk update && apk add wget \
&& apk add freetype-dev make jpeg-dev autoconf gcc g++ \
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
  && docker-php-ext-enable mongodb redis bcmath pdo_mysql \
  && rm -rf /var/cache/apk/* \
&& wget https://mirrors.aliyun.com/composer/composer.phar \
  && mv composer.phar /usr/local/bin/composer && \
chmod a+x /usr/local/bin/composer && \
composer config -g repo.packagist composer https://mirrors.huaweicloud.com/repository/php/
WORKDIR /var/www/
CMD [ "php" ]