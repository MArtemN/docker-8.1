FROM php:8.1-apache

RUN apt-get update && apt-get install -y \
        default-mysql-client zlib1g-dev libzip-dev libicu-dev libxml2-dev \
		libfreetype6-dev libjpeg62-turbo-dev libxpm-dev libwebp-dev libpng-dev \
		graphviz libcurl3-openssl-dev zip openssl curl \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
	&& docker-php-ext-configure gd --with-webp=/usr/include/ --with-jpeg=/usr/include/ --with-freetype=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install mysqli

RUN usermod -u 1000 www-data && groupmod -g 1000 www-data

WORKDIR /var/www/html

EXPOSE 9000
