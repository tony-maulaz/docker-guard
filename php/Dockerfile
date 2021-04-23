FROM php:7.4-fpm-alpine

WORKDIR /var/www/html

RUN apk update && apk add --no-cache openldap-dev libzip-dev
RUN docker-php-ext-install pdo pdo_mysql zip ldap

