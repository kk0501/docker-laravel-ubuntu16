FROM fuke0501/ubuntu:v1
MAINTAINER fuke<461025755@qq.com>

VOLUME /app
ENV WEBROOT /app
WORKDIR $WEBROOT

RUN apt-get update -y \
    && LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php -y && apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        build-essential \
        imagemagick \
        ca-certificates \
        libpng12-dev \
        libjpeg-dev \
        php7.1 \
        php7.1-cli \
        php7.1-dev \
        php7.1-bcmath \
        php7.1-bz2 \
        php7.1-fpm \
        php7.1-common \
        php7.1-curl \
        php-imagick \
        php7.1-gd \
        php7.1-intl \
        php7.1-json \
        php-apcu \
        php7.1-mbstring \
        php7.1-mcrypt \
        php7.1-mysql \
        php7.1-xml \
        php7.1-opcache \
        php7.1-zip \
        git vim rsyslog \
    && curl -sL https://deb.nodesource.com/setup_8.x | bash - \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs \
    && npm -g install yarnpkg \
    && mkdir /run/php/ \
    && curl https://getcomposer.org/installer | php -- && mv composer.phar /usr/local/bin/composer && chmod +x /usr/local/bin/composer \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && groupmod --gid 1000 www-data && usermod --uid 1000 --gid 1000 www-data

EXPOSE 9000

CMD ["php-fpm7.1", "--nodaemonize"]