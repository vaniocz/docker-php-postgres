FROM php:7.2-apache

RUN apt-get update && apt-get install -y \
            git \
            zlib1g-dev \
            libicu-dev \
            libfreetype6-dev \
            libjpeg62-turbo-dev \
            libpng-dev \
            libpq-dev \
            gnupg \
            tzdata && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install zip intl gd pgsql pdo_pgsql opcache && \
    pecl install apcu-5.1.8 && \
    docker-php-ext-enable apcu && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* && \
    a2enmod rewrite && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    curl -sS https://deb.nodesource.com/setup_7.x | bash - && \
    apt-get install -y nodejs


COPY php.ini /usr/local/etc/php/
