# FROM php:7.4.9-fpm

# COPY php.ini /usr/local/etc/php/

# RUN apt update \
#   && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip \
#   && docker-php-ext-install pdo_mysql zip

# RUN curl -sS https://getcomposer.org/installer | php \
#   && mv composer.phar /usr/local/bin/composer \
#   && composer self-update

# WORKDIR /var/www

FROM php:7.4.9-fpm

COPY php.ini /usr/local/etc/php/

# ここを修正（sedでリポジトリURL変更 → apt update → 必要なパッケージのインストール）
RUN sed -i 's|http://deb.debian.org/debian|http://archive.debian.org/debian|g' /etc/apt/sources.list \
  && sed -i '/security.debian.org/d' /etc/apt/sources.list \
  && apt update \
  && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip \
  && docker-php-ext-install pdo_mysql zip

RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer \
  && composer self-update

WORKDIR /var/www

