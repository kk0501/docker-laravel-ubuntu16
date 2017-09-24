FROM ubuntu:16.04
MAINTAINER fuke<461025755@qq.com>

ENV MY_TZ=Asia/Shanghai
ENV TERM=xterm

RUN apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y locales python-software-properties software-properties-common \
    && apt-get -qq upgrade \
    && rm -rf /etc/timezone && echo $MY_TZ >> /etc/timezone \
    && locale-gen en_US.UTF-8 && LC_ALL=en_US.UTF-8