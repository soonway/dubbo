#
# MAINTAINER        Songwen Wu <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
# zookeeper version   3.4.6
# Dockerizing zookeeper: Dockerfile for building soonway/zookeeper:3.4.6 images
#

FROM soonway/jre:7u51

MAINTAINER Songwen Wu <wusongwen@126.com>

RUN set -x \
    && mkdir -p /opt/zookeeper \
    && mkdir -p /opt/zookeeper/data \
    && mkdir -p /opt/zookeeper/datalog

#自行在Dockerfile同一目录下面解压zookeeper-3.4.6.tar.gz文件
ADD zookeeper-3.4.6 /opt/zookeeper

ENV PATH $PATH:/opt/zookeeper/bin

EXPOSE 2181 2888 3888

WORKDIR /opt/zookeeper

VOLUME ["/opt/zookeeper/conf", "/opt/zookeeper/data"]

ENTRYPOINT ["/opt/zookeeper/bin/zkServer.sh"]
CMD ["start-foreground"]
