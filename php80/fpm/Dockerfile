FROM phpdockerio/php80-fpm:latest

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
 && apt-get -y --no-install-recommends install php8.0-mysql php8.0-pgsql php8.0-bcmath php8.0-redis php8.0-phpdbg php8.0-igbinary php8.0-intl \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
 && apt-get -y install git \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install xdebug
RUN apt-get update \
 && apt-get -y install php8.0-xdebug \
 && echo '' > /etc/php/8.0/cli/conf.d/20-xdebug.ini \
 && echo '#!/bin/sh\nphp -d zend_extension=xdebug.so "$@"' >> /usr/local/bin/xphp \
 && chmod +x /usr/local/bin/xphp \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
