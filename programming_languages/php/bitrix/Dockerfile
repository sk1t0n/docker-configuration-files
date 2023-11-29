FROM php:8.0-apache

RUN apt update && apt install zip unzip -y && \
    curl -sSLf \
        -o /usr/local/bin/install-php-extensions \
        https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions bcmath ctype fileinfo json mbstring openssl \
    pdo pdo_mysql mysqli tokenizer xml gd imagick opcache intl zip && \
    curl -fsSL https://deb.nodesource.com/setup_18.x | bash && \
    apt install nodejs && \
    rm -rf /var/lib/apt/lists/*

COPY --from=composer /usr/bin/composer /usr/bin/composer

USER 1000:1000

EXPOSE 80
