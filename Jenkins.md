# jenkinsci/blueocean版本安装
+ 参见[使用Maven构建Java应用程序](https://jenkins.io/zh/doc/tutorials/build-a-java-app-with-maven/)

# Jenkins最新版本docker安装
+ [docker安装jenkins最新版本](https://www.cnblogs.com/mrhugui/p/11732397.html)

## 拉取一个jenkins的最新镜像
+ docker pull jenkins/jenkins:lts

## 创建一个jenkins目录
+ mkdir /Users/lvweiwei/docker/jenkins_lts

## 启动Jenkins容器
+ docker run -d  --name jenkins -p 8080:8080 -p 50000:50000 -v /Users/lvweiwei/docker/jenkins_lts:/var/jenkins_home jenkins/jenkins:lts

> 注意：为了数据持久化，采用了-v /Users/lvweiwei/docker/jenkins_lts:/var/jenkins_home
> 
## 登录Jenkins
+ http://ip:8080 or http://localhost:8080
+ 用户名：admin
+ 密码：Passw0rd
+ 全名：admin

## 登录容器shell
+ docker container exec -it jenkins bash

## 启动、关闭脚本
+ 启动脚本：/Users/lvweiwei/docker/startjenkins
+ 关闭脚本：/Users/lvweiwei/docker/stopjenkins

## 在~/.bash_profile中设置Path
+ [MAC 设置环境变量path的几种方法](https://www.jianshu.com/p/2d7a2c705b4a)

## 插件安装
### Publish Over SSH

> 通过SSH实现远程部署

### maven integration

> 可在“新建任务”中增加“构建一个maven项目”选项

### Docker

+ 安装后在“系统管理”->“系统配置”中增加“云”
+ 其中：“Docker Host URI”设置为“tcp://172.16.41.69:2375”

> 172.16.41.69为本机（宿主机）ip地址
> 
> 由于本应用运行在容器中，因此应保证宿主机的docker开放了远程API
> 
> 关于在MAC下如何开放远程API，参见Docker+Kubernetes.md中的说明
> 

+ 使用“系统管理”-> "Docker"对上面设置的“云”进行监控

## *重要参考*
+ [使用Maven构建Java应用程序](https://jenkins.io/zh/doc/tutorials/build-a-java-app-with-maven/)
+ [安装BlueOcean插件](https://www.jianshu.com/p/199e4e6b420d)
+ [Jenkins+maven+docker 解决项目持续集成](https://www.jianshu.com/p/7883c251eb09)

# Jenkins旧版本docker安装(不要安装这个版本，会出现各种问题)
## 安装
+ docker pull jenkins

## 查看镜像
+ docker inspect jenkins

## 启动镜像
+ docker run --name jen -p 8080:8080 -p 50000:50000 -d -v /Users/lvweiwei/docker/jenkins:/var/jenkins_home jenkins

> 注意：为了数据持久化，采用了-v /Users/lvweiwei/docker/jenkins:/var/jenkins_home
> 

## 查看容器
+ docker container ls

## 停止容器
+ docker container stop "container-name"
+ docker container rm "container-name"

## 登录容器shell
+ docker container exec -it <container-name or container-id> bash

## 查看容器日志
+ docker logs -f <container-name or container-id>

## 登录Jenkins
+ http://ip:8080
+ 用户名：admin
+ 密码：Passw0rd
+ 全名：admin

# 问题处理
## 安装后重启输入用户名、密码提示“Jenkins 登录信息无效。请重试”
> 注意：再次登录时，使用上面的Passw0rd作为密码不管用，竟然还需要../secrets/initialAdminPassword中的密码！！！

## 更换插件升级站点
> 原升级站点：http://updates.jenkins-ci.org/update-center.json
> 
> 找到插件管理-> 高级(Tab),找到升级站点下面的url input框，设置为：http://mirror.esuni.jp/jenkins/updates/update-center.json

