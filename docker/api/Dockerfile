FROM php:8.1-fpm

ENV TZ Asia/Tokyo
ENV COMPOSER_ALLOW_SUPERUSER 1

# install Library
RUN apt-get update \
    && apt-get install -y \
      zip unzip zlib1g-dev vim libzip-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \

# add php-extention-module & xdebug
RUN docker-php-ext-install zip pdo_mysql bcmath && \
	pecl install xdebug && \
    docker-php-ext-enable xdebug

# config file COPY
COPY php.ini /usr/local/etc/php/php.ini

# install Composer
COPY --from=composer:2.3 /usr/bin/composer /usr/bin/composer

COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh
# ENTRYPOINT ["docker-entrypoint.sh"]
ENTRYPOINT ["/entrypoint.sh"]

WORKDIR /app