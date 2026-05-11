# From official php image.
FROM php:cli-alpine
# Create a user group and account under id 1000.
RUN addgroup -g 1000 -S user && adduser -u 1000 -D user -G user
# Install quality-of-life packages.
RUN apk add --no-cache bash curl git vim
# Install composer for php deps.
RUN apk add --no-cache composer  php85-session php85-tokenizer php85-pcntl
# Composer uses its php binary, but we want it to use the container's one
RUN rm -f /usr/bin/php84
RUN ln -s /usr/local/bin/php /usr/bin/php84
# Install postgres pdo driver.
RUN apk add --no-cache postgresql-dev && docker-php-ext-install pdo_pgsql
# Install redis driver.
RUN  docker-php-ext-install pcntl
RUN mkdir -p /usr/src/php/ext/redis; \
    curl -fsSL --ipv4 https://github.com/phpredis/phpredis/archive/refs/tags/6.3.0.tar.gz| tar xvz -C "/usr/src/php/ext/redis" --strip 1; \
    docker-php-ext-install redis
# Install nodejs and npm for frontend.
RUN apk add --no-cache nodejs npm
# Prevent container from exiting early.
CMD ["sleep", "infinity"]
