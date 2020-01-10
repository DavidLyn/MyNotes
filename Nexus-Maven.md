---
# Maven
## 安装
### 下载解压到下述目录
- /Users/lvweiwei/Applications/apache-maven-3.6.0

### 配置环境变量
+ 编辑.bash_profile文件

> vi ~/.bash_profile
> 
> 配置maven文件地址：
> 
> export M2_HOME=/Users/lvweiwei/Applications/apache-maven-3.6.0
> 
> export PATH=$PATH:$M2_HOME/bin
> 
> 保存文件，执行如下命令使配置生效：
> 
> source ~/.bash_profile

### 设置本地仓库
+ 创建本地仓库目录： /Users/lvweiwei/Applications/mvnrepository
+ 修改文件：/Users/lvweiwei/Applications/apache-maven-3.6.0/conf/settings.xml

-  <localRepository>/Users/lvweiwei/Applications/mvnrepository</localRepository>

- /Users/lvweiwei/Applications/mvnrepository

## 快照与版本
+ 在使用版本（Release）时，如果 Maven 下载所提到的版本为 data-service:1.0，那么它永远不会尝试在库中下载已经更新的版本1.0。要下载更新的代码，data-service的版本必须要升级到1.1

+ 在使用快照（SNAPSHOT）时，Maven会在每次建立自己的项目时自动获取最新的快照（data-service:1.0-SNAPSHOT

## 私有maven库发布及使用流程
### 环境配置
- idea环境下，如果使用内置maven，需要手动生成settings.xml，并关联。
- 操作如下
- 生成settings.xml 右键pom.xml-Maven-create settings.xml
- File-settings-Maven关联配置
- 勾选 User settings file Override
- 勾选 Local repository Override
- Eclipse环境，生成的settings文件路径C:\Users\用户\.m2\settings.xml

### 在Nexus上创建Repository
- 需要管理用户登录

- 创建Repository

- create Repository 
- maven2(hosted) 
- insert repository name
- allow redepoly
- create

- 编辑本地maven配置文件(<servers>标签下增加如下内容,username及password填上自己的用户名密码即可)

```xml
<server>
	<id>nexus-snapshot</id>
	<username></username>
	<password></password>
</server>
<server>
	<id>nexus-release</id>
	<username></username>
	<password></password>
</server>
```

- 在待deploy项目中的pom.xml文件中增加如下内容,host及port替换为仓库地址和端口

```xml
<distributionManagement>
	<repository>
		<id>nexus-release</id>
		<name>Nexus Release Repository</name>
		<url>http://{host}:{port}/repository/maven-releases/</url>
	</repository>

	<snapshotRepository>
		<id>nexus-snapshot</id>
		<name>Nexus snapshots Repository</name>
		<url>http://{host}:{port}/repository/maven-snapshots/</url>
	</snapshotRepository>
</distributionManagement>
```

#### 使用

在项目pom.xml文件中添加repository信息

```xml
<repositories>
	<repository>
		<id>blablabla</id>
		<url>http://{host}:{port}/repository/{xxxx}/</url>
	</repository>
</repositories>
```

然后就可以像引用其他公共仓库中依赖一样引用我们自己发布的依赖了，例如:

```xml
<dependencies>	
	<dependency>
		<groupId>com.huilianjk</groupId>
		<artifactId>utils</artifactId>
		<version>1.0.0-SNAPSHOT</version>
	</dependency>
</dependencies>
```

---
# Nexus
## 安装及初始化
### 安装镜像
+ 拉取镜像：docker pull sonatype/nexus3

### 查看镜像
+ docker inspect sonatype/nexus3

### 在宿主机上创建数据目录
+ /Users/lvweiwei/docker/nexus

> Blob Stores文件（应该是其内部保存构件actifact的文件格式）的位置：/Users/lvweiwei/docker/nexus/blobs

### 启动镜像
+ docker run -d -p 8081:8081 -p 8082:8082 -p 8083:8083 -p 8084:8084 -v /Users/lvweiwei/docker/nexus:/nexus-data --name nexus3 sonatype/nexus3 

> 8081：nexus3网页端
> 
> 8082：docker(hosted)私有仓库，可以pull和push
> 
> 8083：docker(proxy)代理远程仓库，只能pull
>
> 8084：docker(group)私有仓库和代理的组，只能pull

### 登录Nexus及初始化
+ localhost:8081
+ 初始账号admin的密码位置：/nexus-data/admin.password

> 此处 `nexus-data` 为 `/Users/lvweiwei/docker/nexus`

### 停止、删除容器
+ docker container stop nexus3
+ docker container rm nexus3

### 启动、关闭脚本
+ 启动脚本：/Users/lvweiwei/docker/startnexus
+ 关闭脚本：/Users/lvweiwei/docker/stopnexus

### 与配置相关
+ Nexus默认的端口是8081，可以在/nexus-data/etc/nexus.properties配置中修改

> 此处 `nexus-data` 为 `/Users/lvweiwei/docker/nexus`

## Nexus使用
### 仓库格式(format)
+ maven2 : Java仓库
+ nuget : .net仓库

### 仓库类型(type)
+ proxy 代理仓库，如果自己私有库没有对应的资源(jar等)，就会到这里去找
+ hosted 宿主仓库，是自己的私有库地址。有release和snapshots两种类型，在创建jar包的时候需要指定，是正式发布(release)，还是发布开发版(snapshots)
+ group 管理组，组是Nexus一个强大的特性，它允许你在一个单独的URL中组合多个仓库，比如默认组合：maven-central、maven-release和maven-snapshots

# 网上资料
+ [Maven官方教程](http://maven.apache.org/guides/getting-started/index.html)

+ [Maven教程](https://www.yiibai.com/maven)

+ [Nexus Docker主页](https://hub.docker.com/r/sonatype/nexus3/)

+ [Nexus3 Docker安装部署使用](https://www.jianshu.com/p/ba054bc4f76a)

+ [搭建Nexus私库&使用](https://blog.csdn.net/luozhonghua2014/article/details/81583510)

+ [linux下安装nexus repository及Intellij Idea集成私有maven](https://www.cnblogs.com/iamsach/p/9199602.html)

+ [nexus仓库的基本用法](https://www.cnblogs.com/NYfor2018/p/9079629.html)