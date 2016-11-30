#
# MAINTAINER        Songwen Wu  <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
# nginx version  latest
# Dockerizing nginx: Dockerfile for building soonway/nginx images
#

FROM  nginx:latest
MAINTAINER  Songwen Wu  <wusongwen@126.com>

#指定时区为东八区
ENV TZ "Asia/Shanghai"

ADD nginx.conf /etc/nginx/
ADD conf.d   /etc/nginx/conf.d/

VOLUME ["/var/log/nginx"]

EXPOSE 80 443 

CMD ["nginx", "-g", "daemon off;"]
