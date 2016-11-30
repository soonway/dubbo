# dubbo
由于我们的项目对jdk版本有要求，所以用指定的版本来搭建这套dubbo运行环境。<br>
搭建思路：<br>
1、创建一个基础环境（centos6.6 jre7u51 Aisa/Shanghai）。<br>
2、创建一个网络，nginx、zookeeper、provider、tomcat均运行于该网络。<br>
2、nginx直接用官方的最新版本。<br>
3、基于基础环境搭建zookeeper镜像，单机版，所以用伪集群。<br>
4、基于基础环境搭建provider镜像。<br>
5、基于基础环境搭建tomcat镜像，每个tomcat应用均以此镜像运行容器。<br>
具体运行指令如下。<br>
Docker network create zoo<br>

#zookeeper<br>
docker run -d --name zk1 --network=zoo -v /data/docker/projects/dubbo/zookeeper/zk1/myid:/opt/zookeeper/data/myid:ro  hidoms/zookeeper:3.4.6<br>
docker run -d --name zk2 --network=zoo -v /data/docker/projects/dubbo/zookeeper/zk2/myid:/opt/zookeeper/data/myid:ro  hidoms/zookeeper:3.4.6<br>
docker run -d --name zk3 --network=zoo -v /data/docker/projects/dubbo/zookeeper/zk3/myid:/opt/zookeeper/data/myid:ro  hidoms/zookeeper:3.4.6<br>

#tomcat<br>
docker run --name admin --network=zoo -d -v /data/docker/data/admin:/mnt/webapp hidoms/tomcat:jre7u51<br>
docker run -d --name img --network=zoo -v /data/docker/data/img:/mnt/webapp hidoms/tomcat:jre7u51<br>
docker run --name wap --network=zoo -d -v /data/docker/data/m:/mnt/webapp hidoms/tomcat:jre7u51<br>
docker run --name merchant --network=zoo -d -v /data/docker/data/mc:/mnt/webapp hidoms/tomcat:jre7u51<br>
docker run --name api --network=zoo -d -v /data/docker/data/app:/mnt/webapp hidoms/tomcat:jre7u51<br>
