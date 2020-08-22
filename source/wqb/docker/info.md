---
layout: page
title: 常用命令
group: group-docker
order: 1
sidebar:
  - group-docker
  - blogger
  - toc
date: 2020-08-23 01:51:37
---

## images镜像操作

```bash
# 显示images列表
docker images
# 删除<none>镜像, 清理所有none镜像
docker images prune
# 删除指定镜像
docker rmi redis:6.0   # redis:6.0 == REPOSITORY:TAG

# 构建镜像Dockerfile
docker build -t images_name:images_tag_version .
# 运行镜像
docker run --name test -dp 5000:5000 httpaitest:v1.0  # -d 后台运行返回ID， -p指定端口映射
docker start <CONTAINER ID>
docker restart <CONTAINER ID>
docker stop <CONTAINER ID>
```

## container容器操作

```bash
# 显示容器
docker ps
# 进入容器
docker exec -it <CONTAINER ID> /bin/sh  # /bin/sh（alpine linux）   or   /bin/bash
# 删除容器
docker rm <CONTAINER ID>
```

## docker镜像打包tar

```bash
# 1.打包安装
docker save golang:latest > golang.tar
docker load -i golang.tar

# 2.第二种方式
# docker save -o 要保存的文件名  要保存的镜像
docker save -o golang.tar golang:latest
# docker load --input 文件  或者  docker load < 文件名
docker load < golang.tar
```
