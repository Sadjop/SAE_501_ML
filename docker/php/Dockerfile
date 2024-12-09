FROM php:8.1-apache

RUN apt-get update && apt-get install -y \
    vim \
    locales \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    git \
    unzip \
    && docker-php-ext-install \
    pdo \
    pdo_mysql \
    mysqli \
    intl \
    zip \
    && docker-php-ext-enable intl zip

# Installer Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Configurer Apache
RUN a2enmod rewrite

# Configuration du dossier de travail
WORKDIR /var/www/project

# Copier la configuration de Virtual Hosts
COPY ./vhosts/vhosts.conf /etc/apache2/sites-available/000-default.conf
