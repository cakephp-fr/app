FROM php:7.2-fpm

MAINTAINER cake17 <cake17@cake-websites.com>

# Install modules
RUN apt-get update && apt-get install -y \
    g++ \
    libfreetype6-dev \
    libicu-dev \
    libzip-dev \
    libjpeg62-turbo-dev \
    libpq-dev \
    sqlite3 \
    libmagickwand-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure intl \
    && docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-install opcache \
    && docker-php-ext-install gd \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install zip \
    && apt-get purge --auto-remove -y g++ \
    && rm -rf /var/lib/apt/lists/*

# a decommenter pour debugger avec xdebug
RUN pecl install xdebug-2.7.2 \
    && docker-php-ext-enable xdebug
COPY php.ini.sample /usr/local/etc/php/php.ini

RUN usermod -u 1000 www-data
