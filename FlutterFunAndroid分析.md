---
# 概述

## 项目概述

+ [产品级Flutter开源项目，FunAndroid](https://www.wanandroid.com/blog/show/2660)

## 本机位置

+ `/Users/lvweiwei/demos/fun_android_flutter`

---
# 问题处理

## Gradle编译失败

+ 修改 android/build.gradle 中 buildscript 和 allprojects

```
google()
jcenter()
```

> 修改为

```
maven { url 'https://maven.aliyun.com/repository/google' }
maven { url 'https://maven.aliyun.com/repository/jcenter' }
maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
```

## Android模拟器的使用

+ 好像必须先启动，然后在 `Flutter Device Selection` 中采用出现。而IOS模拟器可在 `Flutter Device Selection` 中选择并启动

+ 本机安装的 Android 虚拟设备好像有的版本太低不能用？？？


---
# 相关技术分析

## fluro 路由搭建 ???

+ 参考资料

> [Flutter中fluro使用](https://www.jianshu.com/p/e575787d173c)

## jpush_flutter 极光推送 ???


## dio 封装全局请求 拦截登录 打通webview与app交互 ???

## flutter_webview_plugin 接 webview

---
# 延伸技术点

## 状态管理 Provider

+ 比较好的参考资料：[Flutter 状态管理指南之 Provider](https://zhuanlan.zhihu.com/p/70280813?from_voters_page=true)

+ Provider 的目标就是完全替代 StatefulWidget

## i8n ???


## extends,mixin,implements,abstract总结

+ 继承  extends

> dart 里的继承是单继承，即只能又一个父类
> 
> 子类会继承父类所有非私有属性和方法
> 
> 子类重写父类的方法用 @override，子类调用父类方法用 super

+ 混合 mixin（with）

> mixin 不能有构造函数
> 
> 一个类可以 mixin 多个 mixin 类
> 
> mixin 不是继承

+ 接口实现 implements

> 每个类都是一个隐式接口，包含所有的属性和方法
> 
> 当一个类被 implements ， 子类需要重写该类的所有属性和方法，并在前面加 @override

+ 抽象类 abstract

> 不能被实例化，只能被子类继承
> 
> 可以在抽象类中定义抽象方法与普通方法，抽象方法不能有实现，且子类必须重写该方法，而普通方法不强制子类重写

---
# 源代码分析

## pubspec.yaml

+ name: fun_android

> 相当于定义了一个名称为 `fun_android` 的 package，因此在代码中有下述代码：

```
import 'package:fun_android/config/storage_manager.dart';
```

