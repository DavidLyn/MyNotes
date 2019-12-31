# Pacemaker
## Pacemaker功能
+ 对于任何形式的软件资源，通过为其自定义资源启动与管理脚本（资源代理），几乎都能作为资源对象而被 Pacemaker管理
+ Pacemaker仅是资源管理器，并不提供集群心跳信息，由于任何高可用集群都必须具备心跳监测机制；Pacemaker的心跳机制主要基于 Corosync或 Heartbeat来实现
+ pacemaker只是作为HA的资源管理器，所以不要想当然理解它能够直接管控资源，如果你的资源没有做脚本配置那么对于pacemaker来说它就是不可管理的


## 参考资料
+ [Pacemaker官网](http://clusterlabs.org/)
+ [Pacemaker文档](https://clusterlabs.org/pacemaker/doc/)
+ [Pacemaker浅析](https://blog.csdn.net/a964921988/article/details/82628478)

# 问题处理
## 报错 corosync [TOTEM ] The network interface is down，以至节点心跳传递不过来
+ 原因：/etc/corosync/corosync.config中的bindnetaddr设置有问题
+ if the local interface is 192.168.5.92 with netmask 255.255.255.0, set bindnetaddr to 192.168.5.0
+  If  the  local  interface  is  192.168.5.92  with  netmask 255.255.255.192,  set  bindnetaddr  to 192.168.5.64
+  参考[corosync+pacemaker做高可用web集群](http://www.bubuko.com/infodetail-366429.html)


## 无法执行crm命令
+ 原因：在rhel6.3以前常用的版本是crmsh, 是一个资源管理器的配置接口，在rhel6.4以后用的是pcs，这里可以两种都用
+ crmsh在centos6.5的yum库中没有，所以要去下载安装crmsh或自己编译安装crmsh
+ 安装crmssh除了下载的几个文件外，还有其他的python的依赖关系，所以用yum localinstall来安装解决依赖关系。把这三个文件放在/root目录下，然后安装
+ # yum --nogpgcheck localinstall  crmsh-2.1-1.6.x86_64.rpm  pssh-2.3.1-4.1.x86_64.rpm  python-pssh-2.3.1-4.1.x86_64.rpm


# 参考链接
+ [corosync+pacemaker实现web集群高可用](https://blog.51cto.com/nmshuishui/1399811)
+ 