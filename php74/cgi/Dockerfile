FROM streakphp/php74-cli:latest

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install CGI
RUN apt-get update \
 && apt-get -y --no-install-recommends install php7.4-cgi \
 && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Open up preferred CGI port
EXPOSE 8080
