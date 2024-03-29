FROM php:8.2-fpm

# Install dependencies
RUN apt-get update \
    && apt-get install -y \
    apt-utils \
    man \
    curl \
    git \
    bash \
    vim \
    zip unzip \
    acl \
    iproute2 \
    dnsutils \
    fonts-freefont-ttf \
    fontconfig \
    dbus \
    openssh-client \
    sendmail \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    icu-devtools \
    libicu-dev \
    libmcrypt4 \
    libmcrypt-dev \
    libpng-dev \
    zlib1g-dev \
    libxml2-dev \
    libzip-dev \
    libonig-dev \
    graphviz \
    libcurl4-openssl-dev \
    pkg-config \
    libldap2-dev \
    libpq-dev \
    && pecl install mongodb \
    && echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongodb-ext.ini \
	&& echo "max_execution_time=300" > /usr/local/etc/php/conf.d/php.ini

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN docker-php-ext-configure intl --enable-intl && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd && \
    docker-php-ext-install pdo \
    pgsql pdo_pgsql \
    mysqli pdo_mysql \
    intl iconv mbstring \
    zip pcntl \
    exif opcache \
    && docker-php-source delete

RUN curl -sL https://getcomposer.org/installer | php -- --install-dir /usr/bin --filename composer

# Рабочая директория для PHP
WORKDIR /var/www/app

CMD ["php-fpm"]
