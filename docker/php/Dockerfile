FROM php:7.4-fpm

COPY php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y git unzip libzip-dev libicu-dev libonig-dev libpq-dev zlib1g-dev mariadb-client vim \
  && docker-php-ext-install intl pdo_mysql zip bcmath pdo_pgsql

RUN pecl install xdebug && \
    docker-php-ext-enable xdebug

#Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www/html

RUN composer global require "laravel/installer"
