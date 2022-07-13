# Docker

Docker 的工作模式就是创建镜像，并且利用镜像创建容器，然后在容器里面配置特定环境进行部署。

[Docker 基本命令_w3cschool](https://www.w3cschool.cn/use_docker/use_docker-cjka27zg.html)

```bash
# 下载
yum -y install docker

# 查询 tutorial 镜像
docker search tutorial

# 拉取下载/推送镜像
docker pull/push ubuntu:20.04

# 列出本地镜像
docker images

# 创建容器
docker run -it --name web -dp 80:80 ubuntu:20.04

# 启动容器
docker start id

# 刷新
apt-get update
apt-get upgrade

# 列出运行容器
docker ps

# 列出所有容器（包括未运行的）
docker ps -a

--name : 指定一个容器的名称（将名称加入到Docker DNS当中）
[root@localhost ~]# docker run -d --name nginx_bak nginx:1.19.5

此时已进入容器内部，所以分别执行hostname、ip addr、env这三个命令可以获取相关信息，如下：

docker commit CONTAINER_ID # 从容器创建镜像

# docker run -d --name mynginx nginx   #启动nginx镜像，没有会自动pull
# docker stop bfd094233f96   #停止一个容器，根据容器 id 进行删除
# docker rm/rmi bfd094233f96   #删除一个容器/镜像
# docker attach d20f3dc6cd92  #进入一个正在运行的容器



通过sudo apt-get install xxxx 安装软件后,总是无法卸载干净,这里以Apache 为例,提供方法:
首先sudo apt-get remove apache2
再sudo apt-get autoremove



```

文件移动

```bash
docker cp mycontainer:/opt/testnew/file.txt /opt/test/

# 从容器拷贝文件到宿主机
docker cp 容器名：容器中要拷贝的文件名及其路径 要拷贝到宿主机里面对应的路径

# 从宿主机拷贝文件到容器
docker cp 宿主机中要拷贝的文件名及其路径 容器名：要拷贝到容器里面对应的路径

# 不管容器有没有启动，拷贝命令都会生效
```

创建镜像（create images）

```bash
# -a author, -m commit -f docker_id name
docker commit -a "jach" -m "80-443-upgrade" -f docker 848358294e70 ubuntu:v1.0

```

退出容器而不停止

ctrl+p+q
