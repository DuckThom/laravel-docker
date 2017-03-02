FROM php:7.1-fpm

ENV XDEBUG_ENABLE 0

ADD ./php.ini /usr/local/etc/php/conf.d
ADD ./php.pool.conf /usr/local/etc/php-fpm.d/
ADD ./docker-php-pecl-install /usr/local/bin

# Install extensions using the helper script provided by the base image
RUN docker-php-ext-install \
    mbstring \
    pdo_mysql \
    tokenizer

RUN docker-php-pecl-install xdebug
ADD xdebug.ini /usr/local/etc/php/conf.d
RUN echo "xdebug.enable_remote=$XDEBUG_ENABLE" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.remote_host=$(/sbin/ip route|awk '/default/ { print $3 }')" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN usermod -u 1000 www-data

WORKDIR /var/www/html

CMD ["php-fpm"]

EXPOSE 9000
