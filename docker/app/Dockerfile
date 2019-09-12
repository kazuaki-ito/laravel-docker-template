FROM php:7-fpm-alpine

ARG UID

RUN mkdir /.composer && chown -R $UID /.composer
WORKDIR /var/www/app

COPY php.ini /usr/local/etc/php/

RUN apk --update add \
    wget \
    curl \
    vim \
    zip \
    unzip \
    libpng \
    libpng-dev \
    libtool \
    make \
    g++ \
    mysql-client \
    imagemagick-dev \
    autoconf \
    pcre-dev

RUN docker-php-ext-install pdo mbstring gd pdo_mysql

RUN pecl install imagick

RUN docker-php-ext-enable imagick

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV COMPOSER_ALLOW_SUPERUSER 1
