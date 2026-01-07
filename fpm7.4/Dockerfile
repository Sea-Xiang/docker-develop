FROM php:7.4-fpm

# 安装系统依赖
RUN apt-get update && apt-get install -y \
    bash \
    bash-completion \
    git \
    openssh-client \
    unzip \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libxml2-dev \
    vim

# 安装核心扩展
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
        gd \
        pdo_mysql \
        mbstring \
        exif \
        zip \
        pcntl \
        bcmath \
        opcache \
        sockets \
        fileinfo

# 安装 Yaf 和 Yac
RUN pecl install yaf-3.3.5 \
    && pecl install yac-2.3.1 \
    && docker-php-ext-enable yaf yac

# 安装 Redis 扩展
RUN pecl install redis-5.3.7 \
    && docker-php-ext-enable redis

# 安装 Composer
RUN curl -sS https://getcomposer.org/installer | php -- \
    --install-dir=/usr/local/bin \
    --filename=composer

EXPOSE 9000
CMD ["php-fpm"]