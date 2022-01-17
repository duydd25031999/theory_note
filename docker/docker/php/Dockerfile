FROM php:7.3-fpm

# cài đặt và kích hoạt opcache, mysqli, pdo_mysql, memcached
RUN apt-get update -y
RUN docker-php-ext-install mysqli 
RUN docker-php-ext-install pdo_mysql

WORKDIR /home/site/site1

# ADD ./php.ini /usr/local/etc/php/php.ini

# EXPOSE 9000

# CMD [ "httpd-foreground"]