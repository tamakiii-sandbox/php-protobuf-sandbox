FROM php:7.3.3-fpm-stretch

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $PHPIZE_DEPS git \
      less && \
    rm -r /var/lib/apt/lists/*

# TODO: Multi-stage build
RUN mkdir -p /tmp && cd $_ && \
    curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v3.7.0/protobuf-all-3.7.0.tar.gz && \
    tar -zxvf protobuf-all-3.7.0.tar.gz && \
    cd protobuf-3.7.0 && \
    ./configure && \
    make && \
    make check && \
    make install && \
    ldconfig && \
    rm -rf /tmp/protobuf*

RUN pecl install protobuf && docker-php-ext-enable protobuf
