FROM fuke0501/ubuntu
MAINTAINER fuke<461025755@qq.com>

VOLUME /app
ENV WEBROOT /app
WORKDIR $WEBROOT

RUN apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        build-essential \
        imagemagick \
        ca-certificates \
        libpng12-dev \
        libjpeg-dev \
        php7.0 \
        php7.0-cli \
        php7.0-dev \
        php7.0-bcmath \
        php7.0-bz2 \
        php7.0-fpm \
        php7.0-common \
        php7.0-curl \
        php-imagick \
        php7.0-gd \
        php7.0-intl \
        php7.0-json \
        php-apcu \
        php7.0-mbstring \
        php7.0-mcrypt \
        php7.0-mysql \
        php7.0-xml \
        php7.0-opcache \
        php7.0-sqlite3 \
        php7.0-zip \
        php-redis \
        git vim rsyslog \
    && mkdir /run/php/ \
    && groupmod --gid 1000 www-data && usermod --uid 1000 --gid 1000 www-data

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs \
    && npm -g install yarnpkg \
    && curl https://getcomposer.org/installer | php -- && mv composer.phar /usr/local/bin/composer && chmod +x /usr/local/bin/composer \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

EXPOSE 9000

CMD ["php-fpm7.0", "--nodaemonize"]