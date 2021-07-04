FROM php:7.3-fpm

COPY ./docker/backend/php.ini /usr/local/etc/php/

USER root

RUN apt-get update \
    && apt-get install -y unzip libzip-dev zlib1g-dev mariadb-client nodejs npm libicu-dev libxslt-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) zip pdo_mysql intl gd xsl

#Update Node.js
RUN npm install n -g \
    && n stable \
    && apt purge -y nodejs npm

#Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === file_get_contents('https://composer.github.io/installer.sig')) { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --version=1.10.10 \
    && php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

COPY ./backend /var/www

WORKDIR /var/www

RUN composer global require "laravel/installer"
