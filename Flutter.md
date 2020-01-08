---
# 安装flutter
## 安装flutter SDK
+ 步骤一: [下载](https://flutter.dev/docs/get-started/install/macos)
+ 步骤二: cd ~/Applications
+ 步骤三: unzip ~/Downloads/flutter_macos_v1.12.13+hotfix.5-stable.zip
+ 步骤四: 在~/.bash_profile中添加:

> FLUTTER_HOME=/Users/lvweiwei/Applications/flutter
> 
> export PATH=$PATH:$FLUTTER_HOME/bin
> 

+ 步骤五: source ~/.bash_profile

## 安装Android Studio相关

+ 运行flutter doctor检查缺失项
+ **Android toolchain** 在Android Studio中提示安装Android SDK 28 and the Android BuildTools 28.0.3

> 主菜单 [Tools] -> SDK Manager -> SDK Platforms tab -> 选择安装Android SDK version 29.0.2可以解决
> 
> 注意： 可选择右下角 Show Package Details，列出所有版本记录

+ **Android Studio** 安装flutter、Dart Plugins

> 打开Android Studio -> Preference > Plugins
> 在搜索框中搜索 Flutter
> 本地没有, 就联网查找,搜索到Flutter, 点击安装即可
> Dart环境他自动会安装好

+ **Xcode** 报错: ✗ CocoaPods installed but not working.

> re-install CocoaPods : sudo gem install cocoapods 可解决

+ **VS Code **

> 在Extensions中搜索Flutter并下载

# flutter操作
## 查看Flutter SDK分支
+ flutter channel
+ flutter packages get获取项目所有的依赖包
+ flutter packages upgrade 获取项目所有依赖包的最新版本


## 升级Flutter SDK和依赖包
+ flutter upgrade

# 网上资源
+ [Flutter 官网](https://flutter.dev)
+ [Flutter 中文网](https://flutterchina.club)
+ [书: Flutter实战](https://book.flutterchina.club)

# 填坑记录
## 第一次运行flutter命令（如flutter doctor）时，它会下载它自己的依赖项并自行编译。以后再运行就会快得多

## [在Android下运行flutter 卡在Running Gradle task 'assembleDebug'...](https://www.cnblogs.com/wupeng88/p/11455874.html)
+ 修改项目中`android/build.gradle`文件

```
buildscript {
    repositories {
        //修改的地方
        //google()
        //jcenter()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:3.2.1'
    }
}

allprojects {
    repositories {
        //修改的地方
        //google()
        //jcenter()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
    }
}

rootProject.buildDir = '../build'
subprojects {
    project.buildDir = "${rootProject.buildDir}/${project.name}"
}
subprojects {
    project.evaluationDependsOn(':app')
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

+ 修改Flutter的配置文件, 该文件在`Flutter安装目录/packages/flutter_tools/gradle/flutter.gradle`

```
buildscript {
    repositories {
        //修改的地方
        //google()
        //jcenter()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.2.1'
    }
}
```

## 在Idea中dart运行出现：Setting VM flags failed: Unrecognized flags: checked
- Run -> Edit Configurations...中去掉Checked Mode

---
# Dart
+ [A tour of the Dart language](https://dart.dev/guides/language/language-tour)

## 语法要点
### 类和对象
+ 在Dart2里面创建对象时可以省略new关键字

+ Dart具有语法糖，可以将构造函数参数赋值给实例变量

```
class Test {
  num x, y;
  
  // 构造函数运行之前设置x和y
  Test(this.x, this.y);
}
```

+ 命名构造函数

> Java可以做到方法重载（也就是：多个同名不同参数构造函数），但是Dart不可以这么做。Dart提供了命名构造。使用命名构造函数为类实现多个构造函数或提供更多的解释说明

```
class Test{
  num x, y;

  // 命名构造
  Test.help() {
    x = 5;
    y = 10;
    print('x=${x}, y = ${y}');
  }
}
void main(){
  Test.help();// 调用命名构造函数
}
```

+ 初始化列表

> 可以在构造函数体运行之前初始化实例变量，用逗号分隔初始化

```
class Test1 {
  var x, y;
  Test1(var x, var y)
      : x = x,
        y = y {
    print('Test1 有参构造初始化');
  }
}
```
> 命名构造函数的初始化列表

```
class Test2{
  var x,y;
  Test2.from(Map<String, num> json)
      : x = json['x'],
       y = json['y'] {
    print('Test2.from(): ($x, $y)');
  }
}
```

> 可以使用assert在初始化列表用来校验输入参数

```
class Test1 {
  var x, y;

  Test1(var x, var y) : assert(x >= 0) {
    print('Test1(): ($x, $y)');
  }

}
```

### 函数
+ 返回值为void时，可以省略void关键字

### 其他
+ 字符串插值

> $variableName (or ${expression})

+ dynamic 关键字

> dynamic不是实际的type，而是类型检查开关。一个变量被dynamic修饰，相当于告诉static type 系统“相信我，我知道我自己在做什么”

## Dart SDK安装
- brew tap dart-lang/dart
- brew install dart
- brew info dart

