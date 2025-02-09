FROM php:fpm

# Install necessary dependencies
RUN apt-get update \
    && apt-get install -y \
        libfreetype6-dev \
        libjpeg-dev \
        libpng-dev \
        libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg --with-png \
    && docker-php-ext-install gd mysqli zip \
    && docker-php-ext-enable mysqli zip

# Install Xdebug
RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini
