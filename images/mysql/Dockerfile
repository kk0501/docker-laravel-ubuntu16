FROM fuke0501/ubuntu
MAINTAINER luke<461025755@qq.com>

RUN groupadd --gid 1000  -r mysql && useradd  --uid 1000 -r -g mysql mysql
RUN echo "deb http://cn.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse" >> /etc/apt/sources.list \
    && echo "mysql-server mysql-server/root_password password root" | debconf-set-selections \
    && echo "mysql-server mysql-server/root_password_again password root" | debconf-set-selections \
    && apt-get update \
    && apt-get -y install mysql-server-5.7  \
    && mkdir -p /var/lib/mysql  \
    && mkdir -p /var/run/mysqld  \
    && mkdir -p /var/log/mysql  \
    && chown -R mysql:mysql /var/lib/mysql  \
    && chown -R mysql:mysql /var/run/mysqld  \
    && chown -R mysql:mysql /var/log/mysql 

RUN apt-get autoclean \
    && apt-get autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

VOLUME /var/lib/mysql

COPY ./startup.sh /root/startup.sh

RUN chmod +x /root/startup.sh

ENTRYPOINT ["/root/startup.sh"]

EXPOSE 3306
CMD ["/usr/bin/mysqld_safe"]