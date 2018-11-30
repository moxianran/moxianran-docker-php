## 简介
用 Docker 容器服务的方式搭建多版本php环境，易于维护、升级。使用前需了解 Docker 的基本概念，常用基本命令。
可以一条条命令执行docker命令来构建镜像，容器。这里推荐使用 docker-compose 来管理，执行项目，下面是使用流程。

相关软件版本：
- PHP 7.1
- PHP 5.6
- MySQL 5.6
- Nginx 1.15.6
- Redis 5.0
- Mongo 3.2.21-jessie

用到的 PHP 拓展：
- redis 4.2.0
- mongodb 1.5.3
- rdkafka 3.0.5 (依赖librdkafka 0.11.6)
- swoole 4.2.9 (php 7.1)
- swoole 1.10.5 (php 5.6)

## 使用
### docker-compose 构建项目
进入 docker-compose.yml 所在目录：
执行命令：
```
docker-compose up
```  

如果没问题，下次启动时可以以守护模式启用，所有容器将后台运行：  
```
docker-compose up -d
``` 