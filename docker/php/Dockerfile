ARG PHP_VERSION=8.1-fpm

FROM php:${PHP_VERSION}

RUN apt-get update && apt-get install -y \
        libzip-dev \
        zip \
    	build-essential \
    	npm \
	&& docker-php-ext-configure zip \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install pdo pdo_mysql mysqli opcache

RUN npm install npm@latest -g && \
    npm install n -g && \
    n latest

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
#COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY docker/php/php.ini $PHP_INI_DIR/conf.d/php.ini

# Expose the port nginx is reachable on
EXPOSE 9000

WORKDIR /var/www
