FROM php:8.1.18-fpm

RUN apt update && apt-get install -y

RUN apt update && apt-get install -y --no-install-recommends \
        acl \
        libcurl4-openssl-dev \
        procps \
        zip \
        unzip \
        wget \
        git \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev \
        libonig-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev && \
    docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ && \        
    docker-php-ext-install \    
        gd \
        zip \
        intl \
        mysqli \
        pdo \
        pdo_mysql \
        xml \
        curl \
        mbstring \
        opcache

RUN pecl install xdebug-3.2.1 \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable xdebug

# RUN usermod -u 1000 www-data
RUN echo 'deb [trusted=yes] https://repo.symfony.com/apt/ /' | tee /etc/apt/sources.list.d/symfony-cli.list
RUN apt update
RUN apt install symfony-cli

RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

COPY ./docker/xdebug/xdebug.ini $PHP_INI_DIR/conf.d/docker-php-ext-xdebug.ini
COPY ./docker/opcache/opcache.ini $PHP_INI_DIR/conf.d/ddocker-php-ext-opcache.ini

# Node.js
RUN curl -sL https://deb.nodesource.com/setup_20.x -o node_setup.sh && \
    bash node_setup.sh && \
    apt-get install -y nodejs && \
    npm install npm -g

# Yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    apt-get update && \
    apt-get install -y yarn

RUN git config --global user.email "name@mail.com" \ 
    && git config --global user.name "Your Name"
WORKDIR /var/www
