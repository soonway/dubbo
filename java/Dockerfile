#
# MAINTAINER        Songwen Wu <wusongwen@hidoms.com>
# DOCKER-VERSION    1.12.1
#
# Dockerizing jdk: Dockerfile for building jdk7 images
#
FROM centos:6.6
MAINTAINER  Songwen Wu <wusongwen@hidoms.com>

ENV JRE_HOME /opt/jre
ENV PATH /opt/jre/bin:$PATH

ENV TZ "Asia/Shanghai"

RUN mkdir -p /opt/

#请将jre-7u51-linux-x64.tar.gz解压到Dockerfile文件相同的目录下面
COPY jre1.7.0_51 /opt/jre
