FROM php:7.4-apache-buster

# Surpresses debconf complaints of trying to install apt packages interactively
# https://github.com/moby/moby/issues/4032#issuecomment-192327844

ARG DEBIAN_FRONTEND=noninteractive

# Update
RUN apt-get -y update --fix-missing && \
    apt-get upgrade -y && \
    apt-get --no-install-recommends install -y apt-utils && \
    rm -rf /var/lib/apt/lists/*

# Install useful tools and install important libaries
RUN apt-get -y update && apt-get -y --no-install-recommends install \
    nano \
    vim \
    wget \
    dialog \
    libsqlite3-dev \
    libsqlite3-0 \
    zlib1g-dev \
    libzip-dev \
    libpng-dev \
    libicu-dev \
    libonig-dev \
    libcurl4 \
    libcurl4-openssl-dev \
    default-mysql-client \
    build-essential \
    git \
    curl \
    zip \
    openssl \
    less

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP Extensions
RUN docker-php-ext-install mysqli pdo_mysql curl json zip mbstring gettext exif gd

# Install xdebug
RUN pecl install xdebug-2.8.0 && \
    docker-php-ext-enable xdebug

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# WP-CLI
RUN curl -o /usr/local/bin/wp https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x /usr/local/bin/wp

# Enable apache modules
RUN a2enmod rewrite headers

ARG user
ARG uid

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u $uid -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user

# Create log file for xdebug
RUN touch /var/log/xdebug.log \
    && chown $user:$user /var/log/xdebug.log \
    && chmod 755 /var/log/xdebug.log

USER $user
