# [真机调试](https://www.cnblogs.com/wxy990118/p/6545120.html)
## 手机端设置
> 设置->关于手机，不停的点击版本号进入开发者模式，然后退出，可以看到多了一个开发人员选项，点击进入，打开USB调试

## Android Studio设置
> 经验证Hwawei mate10不需特殊设置，当Android Studio上选择Run时，手机上会出现提问框，但进行权限确认时，可能会出现“出现应用遮挡了权限请求界面”，此时把悬浮窗口移开就可以了


# 解决Android Studio Gradle Build Running 特别慢的问题

cd /Users/你的用户名/.gradle目录下新建一个文件名为gradle.properties的文件。
内容为即可解决:
org.gradle.daemon=true
**好像没什么卵用**

[加快gradle的编译速度总结](https://www.jianshu.com/p/200d55b4d40a)

# 从GitHub上下载项目
+ Fork the project on the Github
+ git clone the project on Mac
+ open the project in Android Studio
> gradle building will last for lang time

# 快捷键
## Log快捷键
> 输入logd、logi、logw等后按tab键，就会自动补全一条完整的打印语句

> 在onCreate方法外面输入logt，然后按tab键，就会以当前的类名作为值自动生成一个TAG常量

## override快捷键
+ control+o

## implement快捷键
+ control+I

## 查看方法调用情况
+ control+option+H

# 版本管理
## 分支管理
[AndroidStudio的GitHub分支操作](https://blog.csdn.net/u010937230/article/details/54601383)


# gradle学习
## 使用国内maven库
[参考链接](https://www.zhihu.com/question/37810416)

```
buildscript {
    repositories {
        google()
        //jcenter()
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}

allprojects {
    repositories {
        google()
        //jcenter()
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}
```

**经测试，google()必须被保留**

# 开源库分析
+ [Android通用流行框架大全](https://segmentfault.com/a/1190000005073746)

## ORM分析
### GreenDao
+ [Android GreenDao使用教程](https://blog.csdn.net/qq_38520096/article/details/78833801)
+ [GreenDao官网](http://greenrobot.org/greendao/)

#＃ 混合模式框架分析
[如何做一个有高性能混合开发iOS/Android应用？](https://www.zhihu.com/question/41341371)
### WeX5

### React Native

# Gradle 全局参数定义
[Android Studio:Grade 全局参数定义](https://www.jianshu.com/p/43d3e19e3e87)

# 下载插件Android Material Design Icon Generator

+ 菜单:[Android Studio]->[Preferences]

+ 安装好了，重启AS后就可以使用了。。

+ File - new -- Material design icon.....当然，你也可以 ctrl + alt  + M

+ [android图标解决方案汇总](https://www.jianshu.com/p/d61e6df29fda)


# 配置colorAccent,colorPrimary,colorPrimaryDark,toolbar主题颜色
+ [配置colorAccent,colorPrimary,colorPrimaryDark,toolbar主题颜色](https://blog.csdn.net/chenweijiSun/article/details/52858204?locationNum=7&fps=1)

+ AndroidManifest.xml  ->  android:theme="@style/AppTheme"
+ values -> style.xml
+ style.xml -> <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">

+ [Android资源文件夹下面values/style.xml、values-v19/style.xml、values-v21/style.xml主题调用规则](https://blog.csdn.net/amoscxy/article/details/77943127)

+ values-v19/style.xml—对应api19+手机型号在此调用。 
+ values-v21/style.xml—对应api21+手机型号在此调用。 
+ values/style.xml—对应values-v19和values-v21的style.xml中没有对应主题时默认在此调用。
		
# Android中的主题(Theme)
+ [总结一下Android中主题(Theme)的正确玩法](http://www.cnblogs.com/zhouyou96/p/5323138.html)

+ 在AndroidManifest.xml文件中有<application android:theme="@style/AppTheme">
+ @style/AppTheme是引用的res/values/styles.xml 中的主题样式
+ 也有可能是引用的 res/values-v11/styles.xml 或者 res/values-v14/styles.xml
+ 这是根据运行此程序的手机系统来决定的，如果手机系统的API版本是11以上就是v11/styles.xml，以此类推


# [Android系统主题总结和使用](https://blog.csdn.net/tuke_tuke/article/details/73188426)
+ 


# [Android资源文件简介](https://www.cnblogs.com/jingmo0319/p/5714931.html)

**[参考资料：Dagger2从入门到放弃再到恍然大悟](https://www.jianshu.com/p/39d1df6c877d)**

# Dagger & MVP学习

## about MVP

+ 在mvp中，最常见的一种依赖关系，就是Activity持有presenter的引用，并在Activity中实例化这个presenter，即Activity依赖presenter，presenter又需要依赖View接口，从而更新UI
+ 


## about Dagger
+ 在MainActivity里，之前是直接声明MainPresenter，现在在声明的基础上加了一个注解@Inject，表明MainPresenter是需要注入到MainActivity中，即MainActivity依赖于MainPresenter，要注意的是，使用@Inject时，不能用private修饰符修饰类的成员属性

+ 在MainPresenter的构造函数上同样加了@Inject注解

# 背景选择器
**[Android中selector背景选择器](https://www.cnblogs.com/zhangxia/p/5101486.html)**
+ 在Android开发过程中，经常对某一View的背景在不同的状态下，设置不同的背景，增强用户体验。如果按钮，在按下时，背景变化，如果在代码中动态设置，相对比较麻烦。Android为我们提供了selector背景选择器可以非常方便的解决这一问题

# ToolBar
**[Material Design 之 Toolbar 开发实践总结](https://www.jianshu.com/p/e2ae6aaff696)**

# TabLayout
**[Material Design 之 TabLayout 使用](https://www.jianshu.com/p/13f334eb16ce)**

# ViewPager

