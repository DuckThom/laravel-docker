FROM php:7.0-fpm

ADD ./laravel.ini /usr/local/etc/php/conf.d
ADD ./laravel.pool.conf /usr/local/etc/php-fpm.d/

RUN apt-get update && apt-get install libpq-dev libmcrypt-dev libpng-dev libjpeg62-turbo-dev -y --no-install-recommends

# Configure extensions before building
RUN docker-php-ext-configure gd \
    --enable-gd-native-ttf \
    --with-jpeg-dir=/usr/lib/x86_64-linux-gnu \
    --with-png-dir=/usr/lib/x86_64-linux-gnu

# Install extensions using the helper script provided by the base image
RUN docker-php-ext-install \
    mbstring \
    exif \
    pdo_mysql \
    pdo_pgsql \
    mcrypt \
    gd \
    fileinfo

RUN usermod -u 1000 www-data

WORKDIR /var/www/laravel

CMD ["php-fpm"]

EXPOSE 9000
