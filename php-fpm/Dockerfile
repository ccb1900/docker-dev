FROM php:8-fpm

RUN rm -rf /var/www/html && groupmod -o -g 1000 www-data && \
  usermod -o -u 1000 -g www-data www-data