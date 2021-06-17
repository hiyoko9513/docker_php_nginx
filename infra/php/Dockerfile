FROM php:7-fpm
WORKDIR /var/www/html


COPY php.ini /usr/local/etc/php/php.ini

RUN cd /usr/bin && curl -s http://getcomposer.org/installer \n\
| php && ln -s /usr/bin/composer.phar /usr/bin/composer

RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim \
libpq-dev

# db
RUN docker-php-ext-install pdo_mysql pdo_pgsql mysqli

# xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# mailhog
RUN curl -sSLO https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 \
    && chmod +x mhsendmail_linux_amd64 \
    && mv mhsendmail_linux_amd64 /usr/local/bin/mhsendmail
