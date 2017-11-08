FROM php:7.0.13-apache

# Install required packages
RUN set -x \
    && apt-get update \
    && apt-get install -y \
    wget \
    unzip \
    ca-certificates \
    apt-transport-https \
    git

RUN set -x \
    && apt-get install -y \
    zlib1g-dev \
    libpng-dev \
    libcurl4-openssl-dev \
    && docker-php-ext-install gd zip mbstring tokenizer curl pdo pdo_mysql

# Enableing the Apache2 rewrite module
RUN set -x \
    && a2enmod rewrite

# Cleanup
RUN set -x \
    && rm -rf /var/lib/apt/lists/*