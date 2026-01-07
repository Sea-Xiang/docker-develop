FROM php:8.3-fpm-alpine

RUN apk update && apk add --no-cache git openssh tar gzip libarchive-tools

RUN apk add linux-headers libzip gettext-dev procps graphviz libzip-dev unzip \
    libevent-dev libpng-dev libwebp-dev freetype-dev gmp-dev jpeg-dev build-base \
    zlib-dev openssl-dev autoconf openssh-client git

RUN docker-php-ext-configure gd --with-webp --with-jpeg --with-freetype --enable-gd

RUN docker-php-ext-install pcntl mysqli bcmath pdo pdo_mysql posix sockets sysvshm sysvsem zip fileinfo gd gettext ctype bz2

RUN yes '' | pecl install https://pecl.php.net/get/redis-6.2.0.tgz
RUN pecl install https://pecl.php.net/get/yaf-3.3.6.tgz
RUN pecl install https://pecl.php.net/get/xdebug-3.4.4.tgz
RUN pecl install https://pecl.php.net/get/yac-2.3.1.tgz
RUN pecl install https://pecl.php.net/get/event-3.1.4.tgz
RUN pecl install https://pecl.php.net/get/xhprof-2.3.10.tgz

RUN docker-php-ext-enable yaf yac redis xdebug xhprof \
    pcntl mysqli bcmath pdo pdo_mysql posix sockets sysvshm sysvsem zip fileinfo gd gettext ctype bz2

RUN curl -o composer.phar https://getcomposer.org/download/2.8.9/composer.phar \
    && chmod +x composer.phar \
    && mv composer.phar /usr/local/bin/composer

EXPOSE 9000
CMD ["php-fpm"]