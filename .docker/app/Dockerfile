FROM php:8.0-fpm-buster AS develop

RUN apt-get update \
    && apt-get install -y \
        libpq-dev \
        git \
        zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

#postgres
RUN apt-get install -y libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql \
    && pecl install xdebug-3.0.0 pcov \
    && docker-php-ext-enable xdebug pcov

ADD php.ini $PHP_INI_DIR/conf.d/php-ini-overrides.ini

USER 1000

WORKDIR /app
