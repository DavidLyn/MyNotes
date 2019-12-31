---
# Docker&Docker Compose&Docker Swarm&k8s
+ Docker是容器技术的核心、基础
+ Docker Compose是一个基于Docker的单主机容器编排工具
+ Docker Swarm和Kubernetes是基于Dcoker的跨主机的容器管理平台

---
# Docker安装

## [Docker官网](https://www.docker.com/products/developer-tools)
+ user:lvweiwei
+ pwd:Passw0rd123456
+ e-mail:weiwei.lv@its.cn
+ [docker for mac下载](https://download.docker.com/mac/stable/Docker.dmg)

## Docker仓库
+ [docker中心仓库](http://hub.docker.com)
+ [网易镜像中心](https://c.163yun.com/hub?m=/m/home/#/home)
+ 需要登录网易云：网易云账号 - 13301133157  密码：Password


## 启动远程API

> 默认情况下，Docker守护进程会生成一个socket（/var/run/docker.sock）文件来进行本地进程通信，而不会监听任何端口，因此只能在本地使用docker客户端或者使用Docker API进行操作。 
> 
> 如果想在其他主机上操作Docker主机，就需要让Docker守护进程监听一个端口，这样才能实现远程通信
> 

+ [Linux下的如何配置远程监听*官方*](https://docs.docker.com/install/linux/linux-postinstall/)

### *Mac下的方法（有点复杂！！）*

+ [Docker on Mac上的Remote API 远程控制](https://my.oschina.net/u/2306127/blog/777695)

+ 拉取socat镜像

> docker pull bobrik/socat

+ 运行socat使其开放2375远程访问端口

> docker run --name socat -d -v /var/run/docker.sock:/var/run/docker.sock -p 2375:2375 bobrik/socat TCP4-LISTEN:2375,fork,reuseaddr UNIX-CONNECT:/var/run/docker.sock

+ 测试

> curl localhost:2375/version

+ 启动、关闭脚本

> 启动脚本：/Users/lvweiwei/docker/startsocat

> 关闭脚本：/Users/lvweiwei/docker/stopsocat

---
# Docker使用
## 基本命令
+ 查看版本：docker version
+ 查看本地镜像：docker images
+ 查看信息：docker info

## 与动态配置相关
### SpringBoot应用动态配置
+ [Docker 如何动态给SpringBoot项目传参](https://www.cnblogs.com/coding1024/p/10839833.html)

---
# kubernetes

