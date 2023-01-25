# ベースとなるDockerイメージを指定
FROM php:8.1-fpm-buster

# コンテナ内の環境変数を設定
ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer

# Debian系のパッケージ管理ツールのうち、apt-getを使わないと警告が表示される
RUN apt-get update && \
  apt-get -y install --no-install-recommends git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql bcmath

COPY ./php.ini /usr/local/etc/php/php.ini

# ワークディレクトリを設定
WORKDIR /data