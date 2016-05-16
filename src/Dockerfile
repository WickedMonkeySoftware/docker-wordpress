FROM php:7-apache

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
&&  mv wp-cli.phar /usr/bin/wp \
&&  chmod +x /usr/bin/wp \
&&  wp --allow-root core download \
&&  wp --allow-root core config --dbname=wordpress \
                                --dbuser=root \
                                --dbpass=password123 \
                                --dbhost=mysql \
                                --skip-salts --skip-check \
                                --extra-php="require_once('docker-config.php');"

RUN a2enmod rewrite expires

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* \
&&  docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
&&  docker-php-ext-install gd mysqli opcache

COPY production.ini /usr/local/etc/php/php.ini
COPY docker-config.php /var/www/html/docker-config.php
COPY plugins/ /var/www/html/wp-content/mu-plugins/
COPY run.sh /run.sh
RUN chmod +x /run.sh