FROM php:8.2-fpm

# Installer les extensions nécessaires pour Laravel 10
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libzip-dev \
    libpq-dev \
    libonig-dev \
    libxml2-dev \
    curl \
    unzip \
    git \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
        gd \
        pdo \
        pdo_mysql \
        zip \
        mbstring \
        xml \
        bcmath \
        exif

# Installer Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Configurer user
RUN usermod -u 1000 www-data

WORKDIR /var/www/html

CMD ["php-fpm"]
