# 手册
+ [The MongoDB 4.2 Manual](https://docs.mongodb.com/manual/)

# 1、安装、使用
## 安装mongoDB
+ [docker位置](https://hub.docker.com/_/mongo)
+ docker pull mongo

### 运行
+ docker run --name mongo -p 27017:27017 -p 28017:28017 -d mongo
+ docker run --name mymongo -v /Users/lvweiwei/docker/mongo/data:/data/db -d mongo

> 创建数据挂载目录：/Users/lvweiwei/docker/mongo/data
> 

> MongoDB 提供了简单的 HTTP 用户界面。 如果你想启用该功能，需要在启动的时候指定参数 --rest
> 
> MongoDB 的 Web 界面访问端口比服务的端口多1000
> 
> 如果MongoDB运行端口使用默认的27017，可以在端口号为28017访问web用户界面，即地址为：http://localhost:28017

### 管理
+ docker container exec -it mongo bash
+ mongo

## 安装mongo-express
+ docker pull mongo-express

### 运行
+ docker run --name myexpress --link mymongo:mongo -p 8081:8081 -d mongo-express


### 登录mongo express
+ http://localhost:8081

## 启动、关闭脚本
### mongoDB
+ 启动脚本：/Users/lvweiwei/docker/startmongo
+ 关闭脚本：/Users/lvweiwei/docker/stopmongo

### mongoExpress
+ 启动脚本：/Users/lvweiwei/docker/startexpress
+ 关闭脚本：/Users/lvweiwei/docker/stopexpress

> 注意：mongoExpress启动可能与mongodb之间有一定的时间间隔，不然可能有问题

# 2、基础知识
## 概要
+ 一条记录是一个Document，是一个Json对象
+ 使用collections保存Document，等同于关系数据库中的table
+ 除了collections，还有read only view和On-Demand Materialized Views

# 3、命令说明
## Shell命令

## 系统命令
### 查询Shell版本
+ mongo --version

### 查询db版本
+ mongod --version

