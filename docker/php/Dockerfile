FROM php:5.6.31-fpm

MAINTAINER Nithin Madhuranga <nithin@axis.lk>

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        zip \
        unzip \
        git \
        curl \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg-dev \
        libpng12-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
        libmagickwand-dev \
        && rm -rf /var/lib/apt/lists/* \
        && pecl install imagick-beta \
        && echo "extension=imagick.so" > /usr/local/etc/php/conf.d/ext-imagick.ini \
        && apt-get remove -y \
            libmagickwand-dev \
        && apt-get install -y \
            libmagickwand-6.q16-2 \
        && apt-get -y autoclean

# Install the PHP mcrypt extention
RUN docker-php-ext-install mcrypt

# Install the PHP pdo_mysql extention
RUN docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql

#####################################
# gd:
#####################################

# Install the PHP gd library
RUN docker-php-ext-install gd && \
    docker-php-ext-configure gd \
        --enable-gd-native-ttf \
        --with-jpeg-dir=/usr/lib \
        --with-freetype-dir=/usr/include/freetype2 && \
    docker-php-ext-install gd

WORKDIR /var/www/html/
