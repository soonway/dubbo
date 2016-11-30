# MAINTAINER        Songwen Wu  <wusongwen@hidoms.com>
# DOCKER-VERSION    1.12.1
# tomcat version:   7.0.54
# Dockerizing tomcat: Dockerfile for building tomcat images
#
FROM  hidoms/jre:1.7.0_51
MAINTAINER  Songwen Wu  <wusongwen@hidoms.com>

ENV  TOMCAT_VERSION 7.0.54

RUN mkdir -p /opt/tomcat
ADD apache-tomcat-7.0.54 /opt/tomcat

ENV CATALINA_BASE /opt/tomcat
ENV CATALINA_HOME $CATALINA_BASE
ENV PATH  $PATH:$CATALINA_HOME/bin

COPY server.xml $CATALINA_HOME/conf/server.xml

RUN mkdir -p /mnt/webapp && \
    chmod -R 777 /mnt/

EXPOSE 8080

CMD ["catalina.sh", "run"]
