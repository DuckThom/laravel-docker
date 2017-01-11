FROM php:7.0-fpm

ADD ./php.ini /usr/local/etc/php/conf.d
ADD ./php.pool.conf /usr/local/etc/php-fpm.d/

# Install extensions using the helper script provided by the base image
RUN docker-php-ext-install \
    mbstring \
    pdo_mysql \
    tokenizer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php -r "if (hash_file('SHA384', 'composer-setup.php') === 'aa96f26c2b67226a324c27919f1eb05f21c248b987e6195cad9690d5c1ff713d53020a02ac8c217dbf90a7eacc9d141d') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/local/bin/ && \
    echo "#!/bin/bash \n command=\"/usr/local/bin/composer.phar \$@\" \nsu -s /bin/bash -c \"\$command\" www-data" > /usr/local/bin/composer && \
    chmod +x /usr/local/bin/composer

RUN usermod -u 1000 www-data

WORKDIR /var/www/html

CMD ["php-fpm"]

EXPOSE 9000
