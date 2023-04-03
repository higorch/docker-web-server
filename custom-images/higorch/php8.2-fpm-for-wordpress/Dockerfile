FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    libonig-dev \
    apt-utils \
    libcurl4-openssl-dev \
    libxml2-dev \
    libzip-dev \
    unzip \
    libicu-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    nano \
    git \
    libmagickwand-dev --no-install-recommends && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install \
    dom \
    exif \
    fileinfo \
    mbstring \
    xml \
    opcache \
    intl \
    simplexml \
    pdo_mysql \
    mysqli \
    sockets \
    gd \
    zip \
    curl 

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp

RUN pecl install redis imagick && docker-php-ext-enable redis imagick

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get update && apt-get install -y nodejs \
    && npm install -g yarn

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer