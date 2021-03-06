FROM fuke0501/ubuntu
MAINTAINER luke <461025755@qq.com>

WORKDIR /src

RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php -y && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        imagemagick \
        libfreetype6-dev \
        libmcrypt-dev \
        libcurl4-openssl-dev \
        libpng-dev \
        libmagickwand-dev \
        memcached \
        libmemcached-dev \
        zlib1g-dev \
        libxml2-dev \
        ca-certificates \
        libpng12-dev \
        php7.2 \
        php7.2-cli \
        php7.2-dev \
        php7.2-bcmath \
        php7.2-bz2 \
        php7.2-fpm \
        php7.2-common \
        php7.2-curl \
        php7.2-gd \
        php7.2-intl \
        php7.2-json \
        php7.2-mbstring \
        php7.2-mysql \
        php7.2-xml \
        php7.2-opcache \
        php7.2-sqlite3 \
        php7.2-zip \
        php-apcu \
        php-imagick \
        php-redis \
        php-memcached \
        php-geoip \
        php-xdebug \
    && echo ''| pecl install mcrypt-1.0.1 \
    && echo "extension=mcrypt.so" >  /etc/php/7.2/mods-available/mcrypt.ini \
    && ln -s /etc/php/7.2/mods-available/mcrypt.ini /etc/php/7.2/cli/conf.d/20-mcrypt.ini \
    && ln -s /etc/php/7.2/mods-available/mcrypt.ini /etc/php/7.2/fpm/conf.d/20-mcrypt.ini \
    && mkdir /run/php/

RUN curl -OL https://phar.phpunit.de/phpunit-7.0.phar \
    && chmod +x phpunit-7.0.phar \
    && mv phpunit-7.0.phar /usr/local/bin/phpunit \
    && curl https://getcomposer.org/installer | php -- \
    && mv composer.phar /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer \
    && curl -sL https://deb.nodesource.com/setup_8.x | bash - \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs \
    && npm -g install yarn
RUN groupmod --gid 1000 www-data && usermod --uid 1000 --gid 1000 www-data
RUN apt-get autoclean \
    && apt-get autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 9000

CMD ["php-fpm7.2", "--nodaemonize"]