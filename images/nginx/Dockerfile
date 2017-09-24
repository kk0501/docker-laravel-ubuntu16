FROM fuke0501/ubuntu
MAINTAINER fuke <461025755@qq.com>

VOLUME /app
ENV WEBROOT /app
WORKDIR $WEBROOT

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        nginx-full \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && groupmod --gid 1000 www-data && usermod --uid 1000 --gid 1000 www-data

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]