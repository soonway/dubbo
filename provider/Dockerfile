# MAINTAINER        Songwen Wu  <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
# provider version: jre7u51
# Dockerizing provider: Dockerfile for building wusongwen/provider:jre7u51 images

FROM wusongwen/jre:7u51
MAINTAINER   Songwen Wu  <wusongwen@126.com>

RUN mkdir -p /project

#自行在provider目录下面加上服务方应用目录provider
ADD provider /project/provider
RUN chmod a+x /project/provider/standalone-1.0/bin/*

ENV PATH="$PATH:/project/provider/standalone-1.0/bin"

EXPOSE 20880

CMD ["java","-jar","-Ddubbo.shutdown.hook=true","/project/provider/standalone-1.0.jar"]
