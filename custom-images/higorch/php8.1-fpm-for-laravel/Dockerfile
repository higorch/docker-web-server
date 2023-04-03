FROM php:8.1-fpm

RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    unzip \
    libpq-dev \
    libicu-dev \
    libonig-dev \
    libcurl4-openssl-dev \
    libpng-dev \
    libwebp-dev \
    pkg-config \
    libssl-dev \
    libmagickwand-dev --no-install-recommends && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install \
    bcmath \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    intl \
    mbstring \
    curl \
    zip \
    pcntl \
    gd \
    opcache \
    sockets

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp

RUN pecl install redis imagick && docker-php-ext-enable redis imagick

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get update && apt-get install -y nodejs \
    && npm install -g yarn

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer