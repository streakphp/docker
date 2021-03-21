FROM phpdockerio/php74-fpm:latest

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
 && apt-get -y --no-install-recommends install php7.4-pgsql php7.4-bcmath php7.4-redis php7.4-phpdbg php7.4-igbinary \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
 && apt-get -y install git \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install xdebug
RUN apt-get update \
 && apt-get -y install php7.4-xdebug \
 && echo '' > /etc/php/7.4/cli/conf.d/20-xdebug.ini \
 && echo '#!/bin/sh\nphp -d zend_extension=xdebug.so "$@"' >> /usr/local/bin/xphp \
 && chmod +x /usr/local/bin/xphp \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
