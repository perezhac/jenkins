FROM php:7.1.17-apache
LABEL maintainer="Jaivic"

RUN a2enmod rewrite

RUN apt-get update && apt-get install -y \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libpq-dev \
        libzip-dev \
        libssl-dev \
        libonig-dev \
        vim \
    && docker-php-ext-configure pgsql --with-pgsql=/usr/local/pgsql \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-install -j$(nproc) \
        pdo \
        pdo_mysql \
        pdo_pgsql \
        zip \
        intl \
        soap \
        opcache


COPY  . /var/www/html/
WORKDIR /var/www/html/

