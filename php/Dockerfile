FROM php:8.3-fpm

# Install system dependencies and libraries
RUN apt-get update && apt-get install -y \
    git curl zip unzip \
    libpq-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libssl-dev \
    libicu-dev \
    libmagickwand-dev \
    librabbitmq-dev \
    pkg-config \
    default-mysql-client \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        bcmath \
        exif \
        pcntl \
        gd \
        mbstring \
        opcache \
        pdo \
        pdo_pgsql \
        pdo_mysql \
        soap \
        zip \
        intl \
        sockets \
    && pecl install imagick \
    && pecl install amqp \
    && pecl install redis \
    && pecl install xdebug \
    && docker-php-ext-enable imagick amqp redis xdebug

# Install Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

# Set permissions
RUN chown -R www-data:www-data /var/www \
    && chmod -R 755 /var/www
