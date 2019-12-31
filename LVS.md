# LVS
## [使用LVS实现负载均衡原理及安装配置详解](https://www.cnblogs.com/liwei0526vip/p/6370103.html)
- 有例子，比较翔实

## [四层负载均衡——LVS](https://www.cnblogs.com/chenny7/p/3932738.html)
- 写的比较好

## [LVS持久连接](https://blog.csdn.net/brad_chen/article/details/47837147)

- LVS的持久连接一共分为三种方式

> PCC：将来自于同一个客户端发往VIP的所有请求统统定向至同一个RS
> 
> PPC：将来自于一个客户端发往某VIP的某端口的所有请求统统定向至同一个RS
> 
> PFMC: 端口绑定，port affinity：基于防火墙标记，将两个或以上的端口绑定为同一个服务

## ipvsadm举例

### 使用NAT模式

> 添加地址为207.175.44.110:80的虚拟服务，指定调度算法为轮转。
> 
> ipvsadm -A -t 207.175.44.110:80 -s rr
> 
> 添加真实服务器，指定传输模式为NAT
> 
> ipvsadm -a -t 207.175.44.110:80 -r 192.168.10.1:80 -m
> 
> ipvsadm -a -t 207.175.44.110:80 -r 192.168.10.2:80 -m
> 
> ipvsadm -a -t 207.175.44.110:80 -r 192.168.10.3:80 -m
> 
> NAT模式是lvs的三种模式中最简单的一种。此种模式下只需要保证调度服务器与真实服务器互通就可以运行

### 使用DR模式
+ 设置真实服务器的lo接口不做ARP应答

> echo 1 > /proc/sys/net/ipv4/conf/all/arg_ignore
> 
> echo 1 > /proc/sys/net/ipv4/conf/lo/arg_ignore
> 
> 设置这个选项可以使得各个接口只对本接口上的地址进行响应
> 
> 还需要设置arp_announce选项为2，设置方法同上

+ 在真实服务器上添加虚拟IP

> ifconfig lo:0 192.168.10.10 boradcast 207.175.44.110 netmask 255.255.255.255
>
> ip r add 192.168.10.10 dev lo

+ 添加ipvs规则

> 添加地址为192.168.10.10:80的虚拟服务，指定调度算法为轮转
> ipvsadm -A -t 192.168.10.10:80 -s rr
> 
> 添加真实服务器，指定传输模式为DR
> 
> ipvsadm -a -t 192.168.10.10:80 -r 192.168.10.1:80 -g
> 
> ipvsadm -a -t 192.168.10.10:80 -r 192.168.10.2:80 -g
> 
> ipvsadm -a -t 192.168.10.10:80 -r 192.168.10.3:80 -g
> 
> 注意：此处的例子中客户、调度服务器、真实服务器都是位于同一网段的
> 

## ldirectord
- ldirectord可实现上述对ipvs的设置
- 该配置文件中每一real=行都必须给出gate、masq或ipip指出要使用的转发方法
- [ldirectord.cf文件详解](https://blog.csdn.net/libinbin_1014/article/details/50808685)

## 相关资料
- [iptables介绍](http://www.zsythink.net/archives/1199/)

