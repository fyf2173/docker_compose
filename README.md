## Docker-Compose 公共容器库

包含了常用的容器库，并已经做好了相关的配置，拿来即用。关键配置点 {project} 需要做相关的目录替换，替换项目中真正的路径。docker-compose.yaml 中注释了 depends_on，restart 相关配置，提供灵活的，可任意搭配的容器服务，可情况开启。

- mariadb:latest
- mysql:5.5
- nginx:latest
- php
- redis:latest

注：如需要使用 php 容器，则需要自行构建 php 镜像（已经提供相关Dockerfile），例：docker-compose build php

## 使用技巧

#### 创建数据库

```sh
docker-compose exec mariadb
mysql -u root -p'root' --default-character-set=utf8 -e "CREATE DATABASE IF NOT EXISTS {dbname} DEFAULT CHARSET utf8 COLLATE utf8_general_ci;"
```

#### 连接redis客户端

```sh
docker-compose run --rm redis redis-cli -h host
```