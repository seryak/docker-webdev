# Для начала указываем исходный образ, он будет использован как основа
FROM php:7.2-apache
# устанавливаем дополнительный софт
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        git \  # установили гит
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-install -j$(nproc) mbstring pdo_mysql tokenizer iconv mysqli \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd 

# Необязательная строка с указанием автора образа
MAINTAINER wtolk <web@wtolk.ru>

# Apache modules
RUN a2enmod rewrite