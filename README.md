[toc]
# 我的docker练习项目

## docker安装

## docker常用命令

#### 停止、删除所有的docker容器和镜像

`docker ps -aq` 	列出所有的容器 ID
docker stop $(docker ps -aq)	停止所有的容器
docker rm $(docker ps -aq)		删除所有的容器
docker rmi $(docker images -q)	删除所有的镜像

复制文件
docker cp mycontainer:/opt/file.txt /opt/local/
docker cp /opt/local/file.txt mycontainer:/opt/


`docker image prune --force --all`或者`docker image prune -f -a` : 删除所有不使用的镜像
`docker container prune -f`: 删除所有停止的容器

docker exec -it d35eb2fddef1 /bin/bash




##  docker
```
sudo wget -qO- https://get.docker.com | sh
sudo usermod -a -G docker ice-melt
udo gpasswd -a ${USER} docker
```


1. 创建docker组：sudo groupadd docker
2. 将当前用户加入docker组：sudo gpasswd -a ${USER} docker
3. 重启服务：sudo service docker restart
4. 刷新docker成员：newgrp - docker


前用户比如切换为root，再次切换为jing。然后执行docker-compose up -d就ok了
sudo apt-get install docker-compose
docker-compose up -d
docker info
docker run hello world


```
pip freeze > requirements.txt # 项目目录里
# 编写 Dockerfile 文件


# 制作镜像 
# docker build -t [imagename] [dockerfilepath] 
docker build -t project_coffee_app_service . 
docker build -t d_t .

# 运行镜像
# docker run -p 9011:9011 -d --name c_name imagename
docker run -p 9011:9011 -d --name c_name imagename

```

```
# 列出所有容器的ID
docker ps -aq

docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker rmi $(docker images -q)


docker container prune 
docker image prune


# 复制文件
docker cp mycontainer:/opt/file.txt /opt/local/
docker cp /opt/local/file.txt mycontainer:/opt/



# 进入容器去看
docker exec -it ${容器} /bin/bash
# 本地挂载卷到docker里
docker run -d -p 80:80 -v $PWD/file:/project/template

# 产生仅有数据的容器（可以被多个容器挂载，做到被共享）
docker create -v $PWD/data:/var/mydata --name data_container ubuntu
# -it 交互的方式运行
docker run -it --volumes-from data_container ubuntu /bin/bash

```

##### docker registry

```
docker search whalesay
docker pull docker/whalesay
docker run docker/whalesay cowsay hello...
docker tag docker/whalesay ice-melt/whalesay
docker login
	username:
	password:
docker push ice-melt/whalesay
// hub.docker.com
```

##### docker-compose 安装

mac/windows docker 自带
```
# root 

curl -L https://github.com/docker/compose/releases/download/1.9.0/docker-compose-$(uname -s)-$(uname -m) > /usr/local/bin/docker-compose
ls -l /usr/local/bin/docker-compose 
chmod a+x /usr/local/bin/docker-compose 
docker-compose --version


# 第一次不用build
docker-compose up -d
docker-compose stop
docker-compose rm  # 确定
# 删除过需要build
docker-compose build

```





