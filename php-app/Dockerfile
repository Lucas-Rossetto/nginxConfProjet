FROM php:7.3-fpm

# install the PHP extensions we need
RUN apt-get update; \
	apt-get install -y --no-install-recommends \
		libjpeg-dev \
		libpng-dev \
		libpq-dev \
		libicu-dev \
		libzip-dev \
		php7-common \
		php7-cli \
		php7-fpm
	; \
	\
	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; \
	docker-php-ext-configure intl; \
	docker-php-ext-install -j "$(nproc)" \
		gd \
		opcache \
		pdo_pgsql \
		zip \
		mbstring \
		pdo \
        bcmath \
        intl \
	; \
\

#Installer composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

