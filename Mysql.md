+ 修改表的引擎

> alter table mytable engine=innoDB;

+ 查询表信息

> show table status like 'test'\G

## 查询my.cnf起作用顺序
- which mysqld

> /usr/local/bin/mysqld

- /usr/local/bin/mysqld --verbose --help | grep -A 1 'Default options'

>Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf /usr/local/etc/my.cnf ~/.my.cnf 


## 权限管理
+ [MySQL之权限管理](https://www.cnblogs.com/Richardzhu/p/3318595.html)
+ grant all privileges on *.* to jack@'localhost' identified by "jack" with grant option;

> ALL PRIVILEGES 是表示所有权限，你也可以使用select、update等权限
> 
> ON 用来指定权限针对哪些库和表
> 
> *.* 中前面的*号用来指定数据库名，后面的*号用来指定表名
> 
> TO 表示将权限赋予某个用户
> 
>  jack@'localhost' 表示jack用户，@后面接限制的主机，可以是IP、IP段、域名以及%，%表示任何地方。注意：这里%有的版本不包括本地，以前碰到过给某个用户设置了%允许任何地方登录，但是在本地登录不了，这个和版本有关系，遇到这个问题再加一个localhost的用户就可以了
> 
> IDENTIFIED BY 指定用户的登录密码
> 
> WITH GRANT OPTION 这个选项表示该用户可以将自己拥有的权限授权给别人。注意：经常有人在创建操作用户的时候不指定WITH GRANT OPTION选项导致后来该用户不能使用GRANT命令创建用户或者给其它用户授权
> 
> 可以使用GRANT重复给用户添加权限，权限叠加，比如你先给用户添加一个select权限，然后又给用户添加一个insert权限，那么该用户就同时拥有了select和insert权限
> 
> 

