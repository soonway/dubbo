#
# MAINTAINER        Songwen Wu <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
# jre version   7u51
# Dockerizing jre: Dockerfile for building soonway/jre:7u51 images
#

FROM centos:6.6
MAINTAINER  Songwen Wu <wusongwen@126.com>

ENV JRE_HOME /opt/jre
ENV PATH /opt/jre/bin:$PATH

#指定时区为东八区
ENV TZ "Asia/Shanghai"

RUN mkdir -p /opt/

#请将jre-7u51-linux-x64.tar.gz解压到Dockerfile文件相同的目录下面
COPY jre1.7.0_51 /opt/jre
