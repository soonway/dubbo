# MAINTAINER        Songwen Wu  <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
# tomcat version:   7.0.54
# Dockerizing tomcat: Dockerfile for building soonway/tomcat:jre7u51 images
#
FROM  soonway/jre:7u51
MAINTAINER  Songwen Wu  <wusongwen@126.com>

ENV  TOMCAT_VERSION 7.0.54

RUN mkdir -p /opt/tomcat
ADD apache-tomcat-7.0.54 /opt/tomcat

ENV CATALINA_BASE /opt/tomcat
ENV CATALINA_HOME $CATALINA_BASE
ENV PATH  $PATH:$CATALINA_HOME/bin

COPY server.xml $CATALINA_HOME/conf/server.xml

RUN mkdir -p /opt/webapp && \
    chmod -R 777 /opt/

EXPOSE 8080

CMD ["catalina.sh", "run"]
