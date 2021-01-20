ARG PHP_VERSION=8.0

FROM php:${PHP_VERSION}-fpm-alpine AS symforum_php

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions apcu gd intl pdo_mysql opcache redis xdebug

COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /tmp
RUN find /tmp -type d -exec chmod -v 1777 {} +
