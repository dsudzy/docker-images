FROM php:7.2-apache

# install psql
RUN apt-get update && apt-get install -y libpq-dev
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql
RUN docker-php-ext-install pdo pdo_pgsql

RUN a2enmod rewrite

RUN service apache2 restart

RUN curl -sS https://getcomposer.org/installer | php

RUN mv composer.phar /usr/local/bin/composer

RUN echo '"'"'export PATH="$HOME/config/.composer/vendor/bin:$PATH"'"'"' >> ~/.bashrc
RUN service apache2 restart

RUN apt-get update

RUN apt-get -y install vim

RUN apt-get update
RUN apt-get -y install git

COPY ./000-default.conf /etc/apache2/sites-available/