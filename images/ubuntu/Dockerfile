FROM ubuntu:16.04
MAINTAINER fuke<461025755@qq.com>

ENV MY_TZ=Asia/Shanghai
ENV TERM=xterm

RUN apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        locales \
        python-software-properties \
        software-properties-common \
        tzdata \
    && cp /usr/share/zoneinfo/$MY_TZ  /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata \
    && rm -rf /etc/timezone && echo $MY_TZ >> /etc/timezone \
    && locale-gen en_US.UTF-8 zh_CN.UTF-8 && LC_ALL=en_US.UTF-8 \
    && apt-get autoclean && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV LC_ALL=en_US.UTF-8