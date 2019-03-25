FROM php:7.3.3-fpm-stretch

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $PHPIZE_DEPS git \
      libprotobuf-dev libprotoc-dev protobuf-compiler \
      less && \
    rm -r /var/lib/apt/lists/*

RUN pecl install protobuf && docker-php-ext-enable protobuf
