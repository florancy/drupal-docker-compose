FROM php:8.3-fpm

# Installing dependencies for the PHP modules
RUN set -eux; \
    apt-get update; \
    apt-get upgrade -y; \
    apt-get install -y \
            mariadb-client \
            zip \
            libzip-dev \
            curl \
            libz-dev \
            libpq-dev \
            libjpeg-dev \
            libpng-dev \
            libfreetype6-dev \
            libssl-dev \
            libwebp-dev \
            libxpm-dev \
            libmcrypt-dev \
            libonig-dev; \
    rm -rf /var/lib/apt/lists/

# Installing additional PHP modules
RUN set -eux; \
    docker-php-ext-install mysqli pdo pdo_mysql zip opcache; \
    docker-php-ext-configure gd \
            --prefix=/usr \
            --with-jpeg \
            --with-webp \
            --with-xpm \
            --with-freetype; \
    docker-php-ext-install gd;

# Installing Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Installing Xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
