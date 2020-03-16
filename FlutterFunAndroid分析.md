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

## OKToast

+ 参考资料：[flutter toast插件 OKToast的介绍](https://blog.csdn.net/qq_28478281/article/details/89376768)

+ 在 pubspec 引入

```
dependencies:
  oktoast: ^2.1.7
```

+ 引入

```
import 'package:oktoast/oktoast.dart';
```

+ 在代码中定义 OKToast 组件

> 包裹你的 MaterialApp,不是包裹你的 Scaffold

```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return OKToast( // 这一步
      child: new MaterialApp(
        title: 'Flutter Demo',
        theme: new ThemeData(
          primarySwatch: Colors.blue,
        ),
        home: new MyHomePage(),
      ),
    );
  }
}
```

## pull_to_refresh


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

## MaterialApp 构造方法参数

> 参考：[MaterialApp 详解](https://blog.csdn.net/xsj_blog/article/details/100698777)

+ title

> 在任务管理窗口中所显示的应用名字

+ theme

> 应用各种 UI 所使用的主题颜色

+ color

> 应用的主要颜色值（primary color），也就是安卓任务管理窗口中所显示的应用颜色

+ home

> 应用默认所显示的界面 Widget

+ routes

> 应用的顶级导航表格，这个是多页面应用用来控制页面跳转的，类似于网页的网址

+ initialRoute

> 第一个显示的路由名字，默认值为 Window.defaultRouteName

+ onGenerateRoute

> 生成路由的回调函数，当导航的命名路由的时候，会使用这个来生成界面

+ onLocaleChanged

> 当系统修改语言的时候，会触发这个回调

+ navigatorObservers

> 应用 Navigator 的监听器

+ debugShowMaterialGrid

> 是否显示 Material design 基础布局网格，用来调试 UI 的工具

+ showPerformanceOverlay

> 显示性能标签

+ checkerboardRasterCacheImages 、showSemanticsDebugger、debugShowCheckedModeBanner

> 各种调试开关

## 判断操作系统等环境变量

+ 源文件(**源码中有例子**)

> platform.dart

+ 导入包

```
import 'dart:io';
```

+ 方法

> Platform.isMacOS
> 
> Platform.isLinux
> 
> Platform.isWindows


---
# 源代码分析

## pubspec.yaml

+ name: fun_android

> 相当于定义了一个名称为 `fun_android` 的 package，因此在代码中有下述代码：

```
import 'package:fun_android/config/storage_manager.dart';
```

