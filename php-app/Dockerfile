FROM php:7.3-fpm-alpine
# install the PHP extensions we need
RUN apk upgrade --update  \
	    && apk add --no-cache freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev git postgresql-dev postgresql-client && \
	     docker-php-ext-configure gd \
            --with-gd \
            --with-freetype-dir=/usr/include/ \
            --with-png-dir=/usr/include/ \
            --with-jpeg-dir=/usr/include/ && \
          NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
          docker-php-ext-install -j${NPROC} gd opcache pdo pdo_pgsql  && \
          apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev

	#	php7-common \
	#	php7-cli \
	#s	php7-fpm \

RUN apk upgrade --update
#Installer composer

RUN apk add composer curl

#RUN curl -sS https://getcomposer.org/installer | php
#RUN mv composer.phar /usr/local/bin/composer
#RUN chmod +x /usr/local/bin/composer

#Add Drupal
RUN curl https://drupalconsole.com/installer -L -o drupal.phar
RUN mv drupal.phar /usr/local/bin/drupal
RUN chmod +x /usr/local/bin/drupal

WORKDIR /var/www