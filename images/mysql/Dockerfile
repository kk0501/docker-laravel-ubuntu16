FROM fuke0501/ubuntu:v1
MAINTAINER fuke<461025755@qq.com>

RUN groupadd --gid 1000 mysql && useradd --gid 1000 --no-create-home --shell /usr/sbin/nologin --uid 1000 mysql \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        mysql-server \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

EXPOSE 3306

CMD ["mysqld"]