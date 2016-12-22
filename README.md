# **Docker安装及初级使用**

**简介**：Docker是一个开源的引擎，可以轻松的为任何应用创建一个轻量级的、可移植的、自给自足的容器。开发者在笔记本上编译测试通过的容器可以批量地在生产环境中部署，包括VMs（虚拟机）、bare metal、OpenStack 集群和其他的基础应用平台。 

------

#### 1.CentOS安装docker

yum update

yum install docker

注意：此时执行docker命令如   docker search redis  如果出现错误

-->Segmentation Fault or Critical Error encountered. Dumping core and aborting.
Aborted 需要卸载

解决办法：

yum remove docker

yum install docker-io

启动docker 服务

service docker start

------

#### 2.docker基本命令

1）Docker检索镜像

​	docker search 镜像名

例如：docker search redis



2）镜像下载

​	docker pull 镜像名

例如：docker pull redis



3）本地镜像列表

​	docker images