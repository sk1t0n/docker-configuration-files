FROM php:7.3-cli

WORKDIR /app
COPY composer.json package.json /app/

RUN apt update && apt install zip unzip -y && \
    curl -sSLf \
        -o /usr/local/bin/install-php-extensions \
        https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions bcmath ctype fileinfo json mbstring openssl \
    pdo pdo_mysql pdo_pgsql pdo_sqlite tokenizer xml gd imagick opcache intl zip && \
    curl -fsSL https://deb.nodesource.com/setup_18.x | bash && \
    apt install nodejs && \
    rm -rf /var/lib/apt/lists/*

COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN COMPOSER_ALLOW_SUPERUSER=1 composer install \
    --no-interaction \
    --no-plugins \
    --no-scripts \
    --prefer-dist && \
    npm install

USER 1000:1000

EXPOSE 8000

CMD ["php", "-S", "0.0.0.0:8000", "-t", "./public"]
