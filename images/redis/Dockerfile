FROM fuke0501/ubuntu
MAINTAINER fuke <461025755@qq.com>

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        redis-server \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir /data && chown redis:redis /data
VOLUME /data
WORKDIR /data

EXPOSE 6379

CMD ["redis-server", "/etc/redis/redis.conf"]