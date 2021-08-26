FROM php:7.4-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y libzip-dev mariadb-client openssl libpng-dev libicu-dev libonig-dev libxml2-dev libxslt-dev \
  libjpeg-dev zlib1g-dev libfreetype6-dev

RUN pecl install xdebug \
   && docker-php-ext-enable xdebug

RUN docker-php-ext-configure gd --with-jpeg --with-freetype && \
  docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  pdo_mysql \
  sockets \
  soap \
  xsl \
  zip

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www
