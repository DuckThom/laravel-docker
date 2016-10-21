FROM php:7.0-fpm

ADD ./php.ini /usr/local/etc/php/conf.d
ADD ./php.pool.conf /usr/local/etc/php-fpm.d/

RUN apt-get update && apt-get install libpq-dev libmcrypt-dev -y --no-install-recommends

# Install extensions using the helper script provided by the base image
RUN docker-php-ext-install \
    mbstring \
    exif \
    pdo_mysql \
    pdo_pgsql \
    mcrypt \
    fileinfo

RUN usermod -u 1000 www-data

WORKDIR /var/www/html

CMD ["php-fpm"]

EXPOSE 9000
