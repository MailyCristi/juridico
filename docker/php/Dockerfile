FROM php:8.2-fpm

WORKDIR "/gatewayJuridico"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \ 
&& apt-get install php8.0.5-pdo_pgsql \
&& apt-get -y --no-install-recommends install php8.0.5-pdo_pgsql php8.0.5-gd php-redis \
&& apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /usr/share/doc/* \