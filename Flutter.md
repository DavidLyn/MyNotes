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
+ [Flutter 官网 Docs](https://flutter.dev/docs)
+ [Flutter 中文网](https://flutterchina.club)
+ [书: Flutter实战](https://book.flutterchina.club)
+ [Flutter gallery](https://github.com/flutter/flutter/tree/master/examples/flutter_gallery)

# [Flutter 官网 Docs 笔记](https://flutter.dev/docs)

## [Layouts in Flutter](https://flutter.dev/docs/development/ui/layout)

### Widget 对齐（Aligning widgets）
+ row or column使用`mainAxisAlignment`和`crossAxisAlignment`属性对子widget进行对齐

### 调整尺寸（Sizing widgets）
+ 使用`Expanded` widget可使widget适应row或者column的尺寸
+ `Expanded` widget 的 `flex`可决定当前widget的 `flex factor`

### 紧密排列widgets（Packing widgets）
+ 缺省的，row或column总是在其主轴上占用尽可能多的空间。可通过将row或column的`mainAxisSize`设置为`MainAxisSize.min`，从而将其子widgets排列的更紧密

### 嵌套行和列（Nesting rows and columns）
+ 布局框架允许根据需要将行和列嵌套到行和列中

> 为了最大限度地减少严重嵌套的布局代码可能导致的视觉混乱，可在变量和函数中实现UI片段

### 常用布局widget（Common layout widgets）
+ Standard widgets

> 来自 widgets library
> 
> 可被任何app使用
> 
> 包括：`Container` `GridView` `ListView` `Stack`

+ Material widgets

> 来自 Material library
>
> 只能被 Material app 使用
> 
> 包括：`Card` `ListTile`

+ Container

> 添加 `padding` `margins` `borders`
> 
> 改变背景颜色和图片
> 
> 只能包含一个子widget，但这个子widget可以是Row或者Column，也可以是一个widget树的根

+ GridView

> GridView提供了两个预先制作的列表，也可以构建自己的自定义网格
> 
> 当GridView检测到其内容太长而无法容纳呈现框时，它会自动滚动

+ ListView

> 可水平或垂直布置
> 
> 可配置性低于Column，但更易于使用且支持滚动
> 
> 使用`ListTile`构造`ListView `
> 
> 使用`Divider `进行分割

+ Stack

> 用于一个widget叠加在另一个widget上
> 
> children列表中第一个元素是基础widget，第二个元素是覆盖在第一个元素上的widget
>
> Stack的内容不能滚动

+ Card

> 实现了Material card
> 
> 用于展现相关的信息块
> 
> 接受单子widget，但这个子widget可以是Row，Column，或其他由一系列widget构成的widget
> 
> 用圆角和阴影显示
> 
> Card的内容不能滚动

+ ListTile

> 包含最多3行文本和可选图标的定制Row
> 
> 可配置性不及Row，但易于使用

## [Building layouts](https://flutter.dev/docs/development/ui/layout/tutorial)

+ Step 0 : 创建 app 的基础代码

+ Step 1 : Diagram the layout

> 将布局分解为基础元素
> 
> 识别 Row 和 Column
> 
> 布局包含grid吗？
> 
> 存在覆盖元素吗？
> 
> UI需要tab吗？
> 
> 识别需要 `alignment` `padding` `border` 的区域

+ Step 2 : Implement the title row

+ Step 3: Implement the button row

+ Step 4: Implement the text section

+ Step 5: Implement the image section

+ Step 6: Final touch

## *[Creating responsive apps](https://flutter.dev/docs/development/ui/layout/responsive) ???*


## *[Dealing with box constraints](https://flutter.dev/docs/development/ui/layout/box-constraints)???*

## [Adding interactivity to your Flutter app](https://flutter.dev/docs/development/ui/interactive)

+ Stateful and stateless widgets

> Stateful widgets subclass StatefulWidget
> 
> widget的状态保存在 `State` 对象中，使状态和展现分离。当widget的状态变化时，`State`对象调用`setState()`，通知框架重绘widget

+ 管理状态

> 三种方式：
>
> 1、widget自行管理状态
> 
> 2、由父widget管理
> 
> 3、A mix-and-match approach 混搭法
> 

+ Other interactive widgets

> 可以使用GestureDetector创建自定义的widget的互动性

## [Adding assets and images](https://flutter.dev/docs/development/ui/assets-and-images)

+ asset 类型

> 包括：静态数据（比如json文件）、配置文件、icon、图片（JPEG, WebP, GIF, animated WebP/GIF, PNG, BMP, and WBMP）

+ 指定 asset

> Flutter 使用项目根目录下的 pubspec.yaml 定义app中用到的 asset

```
flutter:
  assets:
    - assets/my_icon.png
    - assets/background.png
```

> 为了包含一个目录下的所有asset，可以使用目录名 + /

```
flutter:
  assets:
    - assets/
```

> 注意，上述只包含当前目录下的asset，子目录下的asset需要单独声明

+ Asset bundling

> 在构建过程中，Flutter将asset放入一个称为`asset bundle`的特殊归档中，应用程序可以在运行时从中读取这些asset

+ Asset variants

> 构建过程支持所谓的 asset variants 概念：可能在不同上下文中显示的资源的不同版本
> 
> 当在pubspec.yaml的assets段设置一个asset的路径后，构建过程会在相邻的子目录中查找同名的任何文件，这些文件也将关联到这个asset上，并被包含在asset bundle中
> 
> 举例：假设应用目录下有下述文件：

```
  .../pubspec.yaml
  .../graphics/my_icon.png
  .../graphics/background.png
  .../graphics/dark/background.png
  ...etc.
```

> 并且 pubspec.yaml包含下述内容：

```
flutter:
  assets:
    - graphics/background.png
```

> 于是`graphics/background.png` 和 `graphics/dark/background.png`都将被包含在 asset bundle中，其中，前者作为主asset，后者作为 variant

> Flutter在选择分辨率合适的图像时使用asset variant

+ Loading assets

> AssetImage了解如何将请求的逻辑asset映射到与当前设备像素比率最接近的asset上。为了使此映射正常工作，应根据特定的目录结构安排asset：

```
  .../image.png
  .../Mx/image.png
  .../Nx/image.png
  ...etc.
```

> Where M and N are numeric identifiers that correspond to the nominal resolution of the images contained within. In other words, they specify the device pixel ratio that the images are intended for.

> 要加载图像，请在widget的构建方法中使用AssetImage类

> 为了从依赖包中加载图像，需要为 AssetImage 提供 package 参数

```
AssetImage('icons/heart.png', package: 'my_icons')
```

> Package 可以选择将asset放在 lib/ 目录下，而不是在 pubspec.yaml 中定义。在此情况下，对于那些需要打包的图像文件，需要在 pubspec.yaml 中定义。假设一个名为 fancy_backgrounds 的Package有下述文件：

```
  .../lib/backgrounds/background1.png
  .../lib/backgrounds/background2.png
  .../lib/backgrounds/background3.png
```

> 为了包含的一个文件， pubspec.yaml 中需做下述定义：

```
flutter:
  assets:
    - packages/fancy_backgrounds/backgrounds/background1.png
```

+ Loading Flutter assets in Android

> 对于Flutter中的assets，Android 的 plugin 可通过下述代码访问：

```
AssetManager assetManager = registrar.context().getAssets();
String key = registrar.lookupKeyForAsset("icons/heart.png");
AssetFileDescriptor fd = assetManager.openFd(key);
```

+ Loading Flutter assets in iOS

> 对于Flutter中的assets，IOS 的 OC plugin 可通过下述代码访问：

```
NSString* key = [registrar lookupKeyForAsset:@"icons/heart.png"];
NSString* path = [[NSBundle mainBundle] pathForResource:key ofType:nil];
```

+ Updating the app icon

> Android : 由Flutter的根目录进入 `.../android/app/src/main/res` ，替换各资源文件夹下面的`ic_launcher.png`

> IOS : 由Flutter的根目录进入 `.../ios/Runner/Assets.xcassets/AppIcon.appiconset`，替换各个 png 文件

+ Updating the launch screen

> Flutter 使用原生平台的机制来显示launch screen，launch screen 将持续显示直至Flutter渲染出应用的第一帧画面

> Android : 切换到`.../android/app/src/main`目录下，通过修改`res/drawable/launch_background.xml`来修改launch screen。可参见[Adding a splash screen and launch screen to an Android app](https://flutter.dev/docs/development/add-to-app/android/add-splash-screen)

> IOS : 切换到`.../ios/Runner`，修改 `Assets.xcassets/LaunchImage.imageset`

## [Navigation and routing](https://flutter.dev/docs/development/ui/navigation)

### [Navigate to a new screen and back](https://flutter.dev/docs/cookbook/navigation/navigation-basics)

+ 在Flutter中，Screen 和 page 被称为 route。在android中，route 相当于 activity，在IOS中，route相当于ViewController。在Flutter中，route只是一个widget

+ 在Flutter中使用 Navigator 切换 route。切换到下一个界面使用 `Navigator.push()`，切换回前一界面使用 `Navigator.pop()`

> FirstRoute 的 build() 方法的 onPressed()：

```
// Within the `FirstRoute` widget
onPressed: () {
  Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => SecondRoute()),
  );
}
```

> SecondRoute 的 onPressed()：

```
// Within the SecondRoute widget
onPressed: () {
  Navigator.pop(context);
}
```

### [Navigate with named routes](https://flutter.dev/docs/cookbook/navigation/named-routes)

+ 在 `MaterialApp` 的构造方法中定义 `initialRoute`(起始route) 和 `routes`(route对照表)。*注意，当 `MaterialApp`  使用 `initialRoute` 时，不要使用 `home` 属性*

```
MaterialApp(
  // Start the app with the "/" named route. In this case, the app starts
  // on the FirstScreen widget.
  initialRoute: '/',
  routes: {
    // When navigating to the "/" route, build the FirstScreen widget.
    '/': (context) => FirstScreen(),
    // When navigating to the "/second" route, build the SecondScreen widget.
    '/second': (context) => SecondScreen(),
  },
);
```

+ 在 `FirstScreen` 的 `onPressed()` 切换到 SecondScreen：

```
// Within the `FirstScreen` widget
onPressed: () {
  // Navigate to the second screen using a named route.
  Navigator.pushNamed(context, '/second');
}
```

+ 在 `SecondScreen` 的 `onPressed()` 返回 FirstScreen：

```
// Within the SecondScreen widget
onPressed: () {
  // Navigate back to the first screen by popping the current route
  // off the stack.
  Navigator.pop(context);
}
```

### [Send data to a new screen](https://flutter.dev/docs/cookbook/navigation/passing-data)

+ 先定义被打开的页面（DetailScreen），重点关注：保存主页面传递过来的数据的属性 todo，以及构造方法可接收主页面传递过来的数据

```
class DetailScreen extends StatelessWidget {
  // Declare a field that holds the Todo.
  final Todo todo;

  // In the constructor, require a Todo.
  DetailScreen({Key key, @required this.todo}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // Use the Todo to create the UI.
    return Scaffold(
      appBar: AppBar(
        title: Text(todo.title),
      ),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Text(todo.description),
      ),
    );
  }
}
```

+ 主页面在定义 `ListView` 的 `ListTile` 的 `onTap()` 时，创建 `DetailScreen` ，并传递Todo数据： 

```
ListView.builder(
  itemCount: todos.length,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(todos[index].title),
      // When a user taps the ListTile, navigate to the DetailScreen.
      // Notice that you're not only creating a DetailScreen, you're
      // also passing the current todo to it.
      onTap: () {
        Navigator.push(
          context,
          MaterialPageRoute(
            builder: (context) => DetailScreen(todo: todos[index]),
          ),
        );
      },
    );
  },
);
```

### [Pass arguments to a named route](https://flutter.dev/docs/cookbook/navigation/navigate-with-arguments)

+ 定义需要传递的参数类

```
// You can pass any object to the arguments parameter.
// In this example, create a class that contains a customizable
// title and message.
class ScreenArguments {
  final String title;
  final String message;

  ScreenArguments(this.title, this.message);
}
```

+ 创建接收参数的 widget，使用 ` ModalRoute.of()` 抽取参数

```
// A widget that extracts the necessary arguments from the ModalRoute.
class ExtractArgumentsScreen extends StatelessWidget {
  static const routeName = '/extractArguments';

  @override
  Widget build(BuildContext context) {
    // Extract the arguments from the current ModalRoute settings and cast
    // them as ScreenArguments.
    final ScreenArguments args = ModalRoute.of(context).settings.arguments;

    return Scaffold(
      appBar: AppBar(
        title: Text(args.title),
      ),
      body: Center(
        child: Text(args.message),
      ),
    );
  }
}
```

+ 在 MaterialApp widget 上注册 route 表

```
MaterialApp(
  routes: {
    ExtractArgumentsScreen.routeName: (context) => ExtractArgumentsScreen(),
  },
);
```

+ 在主页面 widget 上通过 `Navigator.pushNamed` 传递参数的方式切换到前述 widget

```
// A button that navigates to a named route. The named route
// extracts the arguments by itself.
RaisedButton(                                                   
  child: Text("Navigate to screen that extracts arguments"),    
  onPressed: () {                                               
    // When the user taps the button, navigate to a named route 
    // and provide the arguments as an optional parameter.      
    Navigator.pushNamed(                                        
      context,                                                  
      ExtractArgumentsScreen.routeName,                         
      arguments: ScreenArguments(                               
        'Extract Arguments Screen',                              
        'This message is extracted in the build method.',       
      ),                                                                                                                 
    );                                                          
  },                                                            
),      
```

### [Return data from a screen](https://flutter.dev/docs/cookbook/navigation/returning-data)

+ 在主页面放置后续定义选择按钮，点击后打开次级页面，同时等待次级页面的返回值，最后将返回值显示在 `SnackBar` 上

```
class SelectionButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return RaisedButton(
      onPressed: () {
        _navigateAndDisplaySelection(context);
      },
      child: Text('Pick an option, any option!'),
    );
  }

  // A method that launches the SelectionScreen and awaits the
  // result from Navigator.pop.
  _navigateAndDisplaySelection(BuildContext context) async {
    final result = await Navigator.push(
      context,
      MaterialPageRoute(builder: (context) => SelectionScreen()),
    );

    // After the Selection Screen returns a result, hide any previous   snackbars
    // and show the new result.
    Scaffold.of(context)
      ..removeCurrentSnackBar()
      ..showSnackBar(SnackBar(content: Text("$result")));
  }
}
```

+ 在次级页面上使用 `Navigator.pop()` 加参数返回，举例如下：

```
RaisedButton(
  onPressed: () {
    // The Yep button returns "Yep!" as the result.
    Navigator.pop(context, 'Yep!');
  },
  child: Text('Yep!'),
);
```

### [Animating a widget across screens](https://flutter.dev/docs/cookbook/navigation/hero-animations)

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
+ [Dart 官方 Docs](https://dart.dev/guides)

## 语法要点
### 基本数据类型

> Dart 属于强类型语言(在Dart2.0之前，Dart是一门弱类型语言。2.0以后变更为强类型语言(注：官网原文是 Dart 2.0 has a sound type system))。同时属于动态类型语言(动态类型语言指只有在运行的时候才会检查数据类型，静态类型语言指编译期间就会检查数类型)，支持闭包
>
>

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

+ 可选参数

> Dart方法有两种类型的参数
> 
> 如果同时包含可选参数和必需参数，必需的参数在参数列表前面， 可选数在后面
> 
> 可选参数可以有一个默认值，当默认值在调用者没有指定值时使用
> 
> 可选参数具体可分为:
> 
> Optional named parameters（可选命名参数）
> 
> Optional positional parameters（可选位置参数）

+ 可选命名参数

> *在方法参数中，使用"{}"包围的参数属于可选命名参数*
> 
> 命名参数中的必要参数要添加@required标注，这样有利于静态代码分析器进行检查

```
  void _buildThree(int num, {String name, int range}) {
    
  }
```
> 可以为可选参数添加默认值

```
  void _buildThree(int num, {String name, int range = 10}) {

  }
```
> 调用包含可选命名参数的方法时，需要使用paramName:value的形式指定为哪个可选参数赋值

```
  _buildThree(10,range: 1);
```

+ 可选位置参数

> 在方法参数中，使用"[]"包围的参数属于可选位置参数

```
  void _buildHouse(int num, [String where, int range]) {

  }
  
  void _buildHouseAndDefaultValue(int num, [String where = 'Shanghai', int range]) {

  }
```

> 调用包含可选位置参数的方法时，无需使用paramName:value的形式，因为 可选位置参数是位置，如果想指定某个位置上的参数值，则必须前面位置的已经有值,即使前面的值存在默认值

```
    _buildHouse(10,10); //不可行的
    
    _buildHouse(10,'shenzhen',10); //可行的
    
    _buildHouseAndDefaultValue(10,10); //不可行的
    
    _buildHouseAndDefaultValue(10,'shenzhen',10); //可行的
```

> 这里特意使用两个不同类型的可选参数作为示例，如果前后可选参数为相同类型，则会出现异常结果，并且只有在发生后才会注意到。所以这一点要特别注意。比如一下示例，假如本意是想赋值给age,但结果将会差强人意

```
void _buildHouse(int num, [int range , int age]) {
  print('range :  $range  age : $age');
}

void main() {
  _buildHouse(10,10);
}

输出：

range :  10  age : null
```

### 其他
+ 字符串插值

> $variableName (or ${expression})

+ dynamic 关键字

> dynamic不是实际的type，而是类型检查开关。一个变量被dynamic修饰，相当于告诉static type 系统“相信我，我知道我自己在做什么”

+ `??` 和 `??=` 操作符

> `AA ?? "999"` 表示如果AA为空，返回999
> 
> `AAA ?= 999` 如果AAA为空，把999赋值给AAA

## Dart SDK安装
- brew tap dart-lang/dart
- brew install dart
- brew info dart

