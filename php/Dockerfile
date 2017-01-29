FROM php:7.0-fpm

RUN apt-get update && apt-get upgrade -y

# RUN npm install -g bower grunt
RUN apt-get install -y git libpng-dev

RUN docker-php-ext-install gd opcache
