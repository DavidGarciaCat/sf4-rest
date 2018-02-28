FROM php:7.2-fpm

MAINTAINER David Garcia <me@davidgarcia.cat>

# Check installed version
# ~~~~~~~~~~~~~~~~~~~~~~~

RUN php -v

# Install dependencies for PHP
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN apt-get update
RUN apt-get install -y openssl git unzip iputils-ping telnet

# Download and install Composer
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer --version

# Enable PHP Memcached Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN apt-get update
RUN apt-get install -y libz-dev libmemcached-dev zlib1g-dev

RUN pecl install memcached

RUN docker-php-ext-enable memcached

RUN echo "extension=memcached.so" > /usr/local/etc/php/conf.d/docker-php-ext-memcached.ini

# Enable PHP Redis Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN pecl install -o -f redis

RUN rm -rf /tmp/pear

RUN docker-php-ext-enable redis

# Enable PHP MySQL Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN docker-php-ext-install pdo pdo_mysql

# Enable PHP XDebug Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug
RUN echo "error_reporting = E_ALL" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "display_startup_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "display_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.idekey=\"PHPSTORM\"" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_port=9001" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
