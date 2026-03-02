FROM php:8.4-fpm

RUN apt-get update && apt-get install -y \
      apt-utils \
      libpq-dev \
      libpng-dev \
      libzip-dev \
      zip unzip \
      git \
      libicu-dev \
      && docker-php-ext-install pdo_mysql bcmath gd zip intl exif pcntl\
      && apt-get clean \
      && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./php/php.ini /usr/local/etc/php/conf.d/php.ini

# composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- --version=2.7.1 \
    --filename=composer \
    --install-dir=/usr/local/bin

# node и npm
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
      && apt-get install -y nodejs \
      && apt-get clean \
      && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www/school-manage

CMD ["php-fpm"]
