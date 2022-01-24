FROM php:8.0-fpm

RUN apt-get update
RUN apt-get install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip
RUN apt-get install -y nodejs npm

RUN pecl install apcu
RUN docker-php-ext-enable apcu 
RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip

WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

