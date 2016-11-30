# dubbo
最近尝试把dubbo项目用docker来运行，由于我们的项目对jdk版本有要求，所以用指定的版本来搭建这套dubbo运行环境。<br>
搭建思路：<br>
&nbsp;&nbsp;项目涉及nginx、tomcat、zookeeper、mysql，为了保证环境的一致性，nginx采用latest版本，tomcat采用7.0.54版本，zookeeper采用3.4.6版本，zookeeper和tomcat用到的java环境统一采用jre7u51版本，mysql采用5.6.33版本，这些容器全部运行在同一个网络里面。<br>
1、创建一个网络zoo，nginx、zookeeper、provider、tomcat均运行于该网络。<br>
2、创建一个基础环境（centos6.6 jre7u51 Aisa/Shanghai）的镜像（soonway/jre:7u51），供zookeeper和tomcat使用。<br>
2、创建一个soonway/nginx镜像，直接用官方的最新版本，加上自己的配置。<br>
3、基于基础环境搭建soonway/zookeeper:3.4.6镜像，创建N+1个容器集群运行。<br>
4、基于基础环境搭建soonway/provider:jre7u51镜像。<br>
5、基于基础环境搭建soonway/tomcat:jre7u51镜像，每个tomcat应用均以此镜像运行容器。<br>
具体运行指令如下。<br>
#zoo网络<br>
创建zoo网络：Docker network create zoo<br>

#基础镜像<br>
在java目录下面运行以下命令：<br>
docker build -t soonway/jre:7u51 .<br>

#zookeeper<br>
创建zookeeper镜像，在zookeeper目录下面运行下面的指令：<br>
docker build -t soonway/zookeeper:3.4.6 .<br>
运行zookeeper容器：<br>
docker run -d --name zk1 --network=zoo -v /projects/dubbo/zookeeper/zk1/myid:/opt/zookeeper/data/myid:ro  soonway/zookeeper:3.4.6<br>
docker run -d --name zk2 --network=zoo -v /projects/dubbo/zookeeper/zk2/myid:/opt/zookeeper/data/myid:ro  soonway/zookeeper:3.4.6<br>
docker run -d --name zk3 --network=zoo -v /projects/dubbo/zookeeper/zk3/myid:/opt/zookeeper/data/myid:ro  soonway/zookeeper:3.4.6<br>

#provider<br>
在provider目录下面创建soonway/provider:jre7u51<br>
docker build -t soonway/provider:jre7u51 .<br>
docker run --name provider --network=zoo -d soonway/provider:jre7u51<br>

#tomcat<br>
在tomcat目录下面创建soonway/tomcat:jre7u51镜像<br>
docker build -t soonway/tomcat:jre7u51 .<br>

docker run --name admin --network=zoo -d -v /project/admin:/opt/webapp soonway/tomcat:jre7u51<br>
docker run -d --name img --network=zoo -v /project/img:/opt/webapp soonway/tomcat:jre7u51<br>
docker run --name wap --network=zoo -d -v /project/m:/opt/webapp soonway/tomcat:jre7u51<br>
docker run --name merchant --network=zoo -d -v /project/mc:/opt/webapp soonway/tomcat:jre7u51<br>
docker run --name api --network=zoo -d -v /project/app:/opt/webapp soonway/tomcat:jre7u51<br>

#mysql<br>
docker run --name mysql --network=zoo -e TZ="Asia/Shanghai" -p 3306:3306 -d -v /project/mysql/mysql.cnf:/etc/mysql/conf.d/mysql.cnf:ro -v /project/mysql:/var/lib/mysql mysql:5.6.33<br>
