# Zookeeper

## 安装

- brew install zookeeper
- 安装目录：/usr/local/Cellar/zookeeper/3.4.13
- 缺省配置文件：/usr/local/etc/zookeeper/zoo.cfg

## 启停服务
- 启动服务：brew services start zookeeper
- 关闭服务：brew services stop zookeeper

## 命令行工具：zkCli
- ls /test : 获取/test节点的所有子节点
- get /test : 获取/test节点的数据内容和属性信息
- create -e /test 123 : 创建临时节点，会话结束后节点将被删除
- create /test 123 : 创建永久节点
- set /test 345 : 更新节点
- delete /test : 删除节点

## telnet登陆
- telnet localhost 2181
- 使用四字命令查询状态[zookeeper四字命令](https://www.cnblogs.com/kuku0223/p/8428341.html)


# 读书笔记
## 《ZooKeeper分布式过程协同技术详解》

- P28

> 分布式的系统通讯有两种方式：直接通过网络进行信息交换；读写某些共享存储
> 
> Zookeeper使用共享存储来实现应用间的协作和同步原语
> 

- P33 脑裂（split-brain）

> 分布式系统中两个或多个部分开始独立工作，导致整体行为不一致性
> 

- P49 znode的四种类型：持久的（persistent）、临时的（ephemeral）、持久有序、临时有序

- P52 客户端可以设置多种监视点：监控znode的数据变化、监控znode的子结点变化、监控znode的创建或删除
- P57 当客户端通过某种语言套件创建一个Zookeeper句柄时，它就会通过服务建立一个会话。客户端初始连接到Zookeeper服务器集合中的某一个服务器上。当通讯不正常时，Zookeeper客户端库会透明的将会话转移到不同的服务器上
- 


