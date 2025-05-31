FROM php:8.3-cli

WORKDIR /app

RUN apt-get update && apt-get install -y unzip git \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && rm composer-setup.php

COPY composer.json composer.lock ./
RUN composer install --prefer-dist --no-interaction

COPY . .

CMD ["composer", "test"]
