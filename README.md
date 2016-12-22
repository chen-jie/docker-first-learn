# **Docker安装及初级使用**

**简介**：Docker是一个开源的引擎，可以轻松的为任何应用创建一个轻量级的、可移植的、自给自足的容器。开发者在笔记本上编译测试通过的容器可以批量地在生产环境中部署，包括VMs（虚拟机）、bare metal、OpenStack 集群和其他的基础应用平台。 

​	Docker支持将软件编译成一个镜像，在这个镜像里面做好的UI软件的各种配置，然后发布这个镜像，使用者可以运行这个镜像，运行中的镜像称之为容器，容器的启动时非常快的，一般以秒为单位。这个有点像我们平时安装ghost操作系统。

------

#### 1.CentOS安装docker

`yum update`

`yum install docker`



**注意：**此时执行docker命令如   docker search redis  如果出现错误

-->Segmentation Fault or Critical Error encountered. Dumping core and aborting.
Aborted 需要卸载

**解决办法：**

`yum remove docker`

`yum install docker-io`



**启动docker 服务**

`service docker start`

------

#### 2.Docker镜像命令

**1）Docker检索镜像**

​	docker search 镜像名

例如：`docker search redis`



**2）镜像下载**

​	docker pull 镜像名

例如：`docker pull redis`



**3）本地镜像列表**

​	`docker images`



**4）镜像删除**

​	`docker rmi image-id`（根据镜像ID删除）

------

#### 3.Docker容器命令

> A *container* is a running instance of an image
>
> 运行中的镜像成为容器

**1）运行容器**

​	docker run --name container-name -d image-name

​	--name后面的参数是为容器取的名称

​	-d表示detached，意味着执行完这个命令后控制台不会被阻塞

例如：`docker run --name test-redis -d redis`



**2）查看运行中容器列表**

​	docker ps 

​	`docker ps -a` 查看运行和停止的



**3）启动和停止容器**

​	`docker stop [container-name|container-id]`   通过容器名称或者容器ID停止容器

​	`docker start[container-name|container-id]`   通过容器名称或者容器ID启动容器



**4）端口映射**

​	Docker容器中运行软件所使用的端口，在本机和本机所在的局域网中是本能访问的，需要将Docker容器中所使用的端口映射到当前主机的端口上。

​	docker run -d -p 6378:6379 --name port-redis redis

​	第一个是当前主机端口，后面是容器中所使用的端口



**5）删除容器**

 	`docker rm container-id`

​	`docker rm $(docker ps -a -q)` 删除所有容器



**6）容器日志**

​	docker logs [contanier-id|contaner-name] 根据容器ID或容器名称查看日志

例如:	`docker logs test-redis`



**7）登录容器**

​	运行中的容器其实是一个功能完备的Linux操作系统。

​	`docker exec -it [container-id|container-name] bash`

​	