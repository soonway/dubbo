#
# MAINTAINER        Songwen Wu  <wusongwen@126.com>
# DOCKER-VERSION    1.12.1
#
# Dockerizing nginx: Dockerfile for building nginx images
#
FROM  nginx:latest
MAINTAINER  Songwen Wu  <wusongwen@126.com>
ENV TZ "Asia/Shanghai"
ADD nginx.conf /etc/nginx/
ADD conf.d   /etc/nginx/conf.d/
VOLUME ["/var/log/nginx"]
EXPOSE 80 443 
CMD ["nginx", "-g", "daemon off;"]
