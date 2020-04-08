FROM php:5.6-fpm
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev
RUN docker-php-ext-install pdo pdo_mysql bcmath zip
