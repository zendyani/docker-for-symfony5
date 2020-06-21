FROM php:7.4-fpm-alpine

COPY wait-for-it.sh /usr/bin/wait-for-it
COPY symfony /usr/bin/symfony

RUN chmod +x /usr/bin/wait-for-it
RUN chmod +x /usr/bin/symfony

RUN apk --update --no-cache add git postgresql-dev

RUN docker-php-ext-install pdo_mysql pdo pdo_pgsql

RUN apk add --update pcre-dev $PHPIZE_DEPS \
        && pecl install redis \
        && docker-php-ext-enable redis.so

RUN apk add --update icu-dev \
	    && docker-php-ext-install intl

RUN apk add --update libxslt-dev libgcrypt-dev \
        && docker-php-ext-install xsl

RUN apk add --update libpng-dev \
        && docker-php-ext-install gd

RUN apk add --update rabbitmq-c-dev \
        && apk add --update --virtual .phpize-deps $PHPIZE_DEPS \
        && pecl install -o -f amqp \
        && docker-php-ext-enable amqp \
        && apk del .phpize-deps 

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www

CMD composer install ; php-fpm 

EXPOSE 9000
