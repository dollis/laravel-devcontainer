# From official php image.
FROM php:8.5-fpm-alpine
RUN apk add --no-cache php85-session php85-tokenizer php85-pcntl
# Install postgres pdo driver.
RUN apk add --no-cache postgresql-dev && docker-php-ext-install pdo_pgsql 
RUN  docker-php-ext-install pcntl

# Install redis driver.

RUN mkdir -p /usr/src/php/ext/redis; \
    curl -fsSL --ipv4  https://github.com/phpredis/phpredis/archive/refs/tags/6.3.0.tar.gz | tar xvz -C "/usr/src/php/ext/redis" --strip 1; \
    docker-php-ext-install redis
