# MQTT & EMQ X

## EMQ X

+ [EMQ X 手册](https://docs.emqx.io/broker/latest/cn/)

### Docker 安装及运行 EMQ X(**经测试，EMQX 开源版本每次重启会重新创建其内置数据库，因此无法保存之前定义的规则等，所以，目前情况下，做不做宿主机的存储映射没有什么太大意义**)

+ 本地映射

```
docker run -d --name emqx -p 8082:8082 -p 1883:1883 -p 8083:8083 -p 8883:8883 -p 8084:8084 -p 18083:18083 -v /Users/lvweiwei/docker/emqx/data:/opt/emqx/data -v /Users/lvweiwei/docker/emqx/log:/opt/emqx/log  -v /Users/lvweiwei/docker/emqx/etc:/opt/emqx/etc emqx/emqx
```

**注意：默认的 Http Api 管理端口为 8081，由于与 mongo express冲突，改为 8082**

> 通过 /Users/lvweiwei/docker/emqx/etc/plugins/emqx_management.conf 配置文件修改监听端口

+ 非本地映射

```
docker run -d --name emqx -p 8081:8081 -p 1883:1883 -p 8083:8083 -p 8883:8883 -p 8084:8084 -p 18083:18083 emqx/emqx
```

**注意：为了和访问 http api 需映射 -p 8081:8081**

### 进入命令行界面

```
docker exec -it emqx /bin/sh
```

### 创建本地挂载

+ 进入目录：/Users/lvweiwei/docker

> 将 container 中的 /opt/emqx/data 拷贝至宿主机：docker cp emqx:/opt/emqx/data .
> 
> 将 container 中的 /opt/emqx/log 拷贝至宿主机：docker cp emqx:/opt/emqx/log .
> 
> 将 container 中的 /opt/emqx/etc 拷贝至宿主机：docker cp emqx:/opt/emqx/etc .

## 创建启停快捷方式

+ /Users/lvweiwei/docker/startemqx

> 可执行 ：chmod a+x startemqx

```
docker run -d --name emqx -p 1883:1883 -p 8083:8083 -p 8883:8883 -p 8084:8084 -p 18083:18083 emqx/emqx
```

+ /Users/lvweiwei/docker/stopemqx

> 可执行 ：chmod a+x stopemqx

```
docker container stop emqx
docker container rm emqx
```

## Dashboard

+ [EMQ X Dashboard](http://localhost:18083)

+ 默认用户口令

> user : admin
>
> pwd : public

## 认证

+ [HTTP 认证](https://docs.emqx.io/broker/latest/cn/advanced/auth-http.html)

> EMQ X 在设备连接事件中使用当前客户端相关信息作为参数，向用户自定义的认证服务发起请求查询权限，通过返回的 HTTP 响应状态码 (HTTP statusCode) 来处理认证请求
> 
>  启用 emqx_auth_http 插件
> 
> **通过启用 HTTP 认证 可在 springboot 端实现对新连接用户的认证**

## 发布订阅 ACL

+ EMQ X 支持通过客户端发布订阅 ACL 进行客户端权限的管理

+ [HTTP ACL](https://docs.emqx.io/broker/latest/cn/advanced/acl-http.html)

> **采用此方式可实现 发布订阅 ACL 的外置**

## 管理 API

+ [客户端](https://docs.emqx.io/broker/latest/cn/advanced/http-api.html#endpoint-clients)

> *DELETE /api/v4/clients/{clientid}*
> 
> 踢除指定客户端。注意踢除客户端操作会将连接与会话一并终结


## 相关资源
### [emqx in github](https://github.com/emqx/emqx/blob/master/README-CN.md)

### [MQTT入门篇](http://dataguild.org/?p=6817)

+ 主题

> 主题并不需要创建，直接使用就是了
> 
> 主题可以通过通配符进行过滤。其中，+可以过滤一个层级，而#只能出现在主题最后表示过滤任意级别的层级
> 
> building-b/floor-5：代表B楼5层的设备
> 
> +/floor-5：代表任何一个楼的5层的设备
> 
> building-b/#：代表B楼所有的设备
> 
> MQTT 允许使用通配符订阅主题，但是并不允许使用通配符广播

+ 服务质量

> MQTT 支持三种不同级别的服务质量（Quality of Service，QoS）为不同场景提供消息可靠性
> 
> 级别0：尽力而为。消息发送者会想尽办法发送消息，但是遇到意外并不会重试
> 
> 级别1：至少一次。消息接收者如果没有知会或者知会本身丢失，消息发送者会再次发送以保证消息接收者至少会收到一次，当然可能造成重复消息
> 
> 级别2：恰好一次。保证这种语义肯定会减少并发或者增加延时，不过丢失或者重复消息是不可接受的时候，级别2是最合适的

+ 消息类型

> MQTT 拥有 14 种不同的消息类型:
> 
> CONNECT：客户端连接到 MQTT 代理
> 
> CONNACK：连接确认
> 
> PUBLISH：新发布消息
> 
> PUBACK：新发布消息确认，是 QoS 1 给 PUBLISH 消息的回复
> 
> PUBREC：QoS 2 消息流的第一部分，表示消息发布已记录
> 
> PUBREL：QoS 2 消息流的第二部分，表示消息发布已释放
> 
> PUBCOMP：QoS 2 消息流的第三部分，表示消息发布完成
> 
> SUBSCRIBE：客户端订阅某个主题
> 
> SUBACK：对于 SUBSCRIBE 消息的确认
> 
> UNSUBSCRIBE：客户端终止订阅的消息
> 
> UNSUBACK：对于 UNSUBSCRIBE 消息的确认
> 
> PINGREQ：心跳
> 
> PINGRESP：确认心跳
> 
> DISCONNECT：客户端终止连接前优雅地通知 MQTT 代理
> 
		
### [mqtt_client/example/mqtt_browser_client.dart](https://github.com/shamblett/mqtt_client/blob/master/example/mqtt_browser_client.dart)

+ The client identifier (short ClientId) is an identifier of each MQTT client connecting to a MQTT broker. As the word identifier already suggests, it should be unique per broker. The broker uses it for identifying the client and the current state of the client

+ The client identifier can be a maximum length of 23 characters