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
+ docker container exec -it mymongo bash
+ mongo

## 安装mongo-express
+ docker pull mongo-express

### 运行
+ docker run --name myexpress --link mymongo:mongo -p 8081:8081 -d mongo-express


### 登录mongo express
+ [mongo express](http://localhost:8081)

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

# 4、查询命令

## 并列查询`$and`

```
# 条件都成立才可以查询到结果
db.stutent.find({$and:[{name:"小漩涡"},{age:30}]})
```

## 或查询`$or`

```
# 有一个条件成立就可以查询到结果
db.stutent.find({$or:[{name:"绿绿"},{name:"小黑"}]})
```

## 子查询`$all`

>  all后面列表中的元素部分顺序,只要在 test_list 中存在就可以查询到所有结果

```
> db.stutent.find({"test_list":{$all:[1,"五"]}})

{ "_id" : ObjectId("5d2eee1314ff51d814e40365"), "name" : "小漩涡", "age" : 30, "test_list" : [ 1, 2, 3, 4, "五", 1000 ], "hobby" : [ "烫头" ] }
```

## 范围查询`$in`

```
# 只要符合列表中的名字全部查找出来
db.stu.find({name:{$in:["绿绿","黑黑","小红","小黑"]}})
```

## 排序/选取/跳过

```
排序:sort 
db.stu.find().sort({ age:1 }) 1正序 -1倒序

选取:limit
db.stu.find().limit(2) 选取两条数据

跳过:skip
db.stu.find().skip(2) 跳过前两条数据

选择中间两条 or 跳过前N条
db.stu.find().skip(0).limit(2).sort({ age:-1 })

优先级:先排序 - 跳过 - 选取

# 分页
var page = 1
var num = 2
var sk = (page-1) * num
db.stu.find().skip(sk).limit(num).sort({ age:-1 })
```


