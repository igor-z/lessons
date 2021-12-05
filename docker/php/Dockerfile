FROM php:8.0-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip libpq-dev \
    && docker-php-ext-install intl opcache pdo pdo_pgsql \
    && pecl install apcu xdebug-3.0.4 xhprof \
    && docker-php-ext-enable xdebug xhprof apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && rm -rf /tmp/* \
    && mkdir /tmp/xhprof \
    && chown www-data /tmp/xhprof

WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

EXPOSE 9000