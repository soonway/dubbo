FROM centos:6.6

MAINTAINER Wu Songwen <wusongwen@hidoms.com>

ENV JRE_HOME /opt/jre
ENV PATH /opt/jre/bin:$PATH

ENV TZ "Asia/Shanghai"

RUN mkdir -p /opt/

COPY jre-7u51-linux-x64.tar.gz /opt/

RUN yum install -y tar \
    && tar -xzf server-jre-7u51-linux-x64.tar.gz -C /opt/ \
    && mv /opt/server-jre1.7.0_51 /opt/jre \
    && yum erase -y tar \
    && yum clean all \
    && rm -rf /var/cache/yum/* \
    && rm -rf /opt/server-jre-7u51-linux-x64.tar.gz \
    && rm -rf /var/log/*
