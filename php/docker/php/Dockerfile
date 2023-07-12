FROM php:8.0-fpm

WORKDIR /var/www/app

RUN curl -sSLf \
        -o /usr/local/bin/install-php-extensions \
        https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions gd mysqli

COPY --from=composer /usr/bin/composer /usr/bin/composer

USER 1000:1000

CMD ["php-fpm"]
