FROM php:8.2-fpm

WORKDIR /var/www

COPY ./composer.json ./composer.json

RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    && docker-php-ext-install pdo pdo_mysql

COPY --from=composer/composer:latest-bin /composer /usr/bin/composer

RUN composer install
