# 概述

## 项目概述

+ [产品级Flutter开源项目，FunAndroid](https://www.wanandroid.com/blog/show/2660)

## 本机位置

+ `/Users/lvweiwei/demos/fun_android_flutter`

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

