FROM php:7.3-fpm

ENV TZ=Asia/Shanghai

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
	libzip-dev \
	git \
    && docker-php-ext-install -j$(nproc) iconv mysqli pdo_mysql zip pcntl \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN curl -O https://mirrors.aliyun.com/composer/composer.phar && chmod +x composer.phar \
    && mv composer.phar /usr/local/bin/composer

COPY ./php.ini /usr/local/etc/php/conf.d/php.ini
