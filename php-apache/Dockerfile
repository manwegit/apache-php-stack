FROM php:7.2.1-apache

MAINTAINER Manwe

ENV DEBIAN_FRONTEND=noninteractive

# Install Postgre PDO
RUN apt-get update && \
    apt-get install -yq libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql

RUN docker-php-ext-install pdo_mysql mysqli

RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  echo "extension=redis.so" > $PHP_INI_DIR/conf.d/redis.ini


RUN pecl install mongodb \
  && echo "extension=mongodb.so" > $PHP_INI_DIR/conf.d/mongodb.ini

RUN apt-get install -y libxml2-dev && \
    docker-php-ext-install soap
  
RUN apt-get clean -yq && rm -rf /var/lib/apt/lists/*



