# dubbo
由于我们的项目对jdk版本有要求，所以用指定的版本来搭建这套dubbo运行环境。<br>
搭建思路：<br>
1、创建一个基础环境（centos6.6 jre7u51 Aisa/Shanghai）。<br>
2、创建一个网络，nginx、zookeeper、provider、tomcat均运行于该网络。<br>
2、nginx直接用官方的最新版本。<br>
3、基于基础环境搭建zookeeper镜像，单机版，所以未用集群。<br>
4、基于基础环境搭建provider镜像。<br>
5、基于基础环境搭建tomcat镜像，每个tomcat应用均以此镜像运行容器。<br>
具体运行指令如下。<br>
Docker network create zoo<br>
