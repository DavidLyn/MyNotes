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

# *Development*

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

+ 在Flutter中，widget 由它们的底层RenderBox对象呈现。RenderBox由其父级给定约束，并在这些约束内调整自身大小。约束包括最小和最大宽度和高度；尺寸由特定宽度和高度组成

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

+ 在定义API时，对于必须的参数考虑使用 @required 注解。为使用 @required ，需要导入 foundation library ：

```
import 'package:flutter/foundation.dart';
```

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

+ 主页面和次级页面中要实现Hero动画的image都要由Hero包裹，且 tag 必须一致

```
Hero(
  tag: 'imageHero',
  child: Image.network(
    'https://picsum.photos/250?image=9',
  ),
);
```

+ 参见[Flutter Hero动画](https://flutterchina.club/animations/hero-animations/)

## Animations

### [Animations - Introduction](https://flutter.dev/docs/development/ui/animations)

+ Flutter 支持多种动画类型
+ 很多 widget，特别是  Material widgets 自带标准的动画效果，也可以自行修改这些效果

+ 动画类型

> 补间动画（Tween animation）：在补间动画中，定义了开始点和结束点，以及时间线和定义了转换时间和速度的曲线。框架计算如何从起点过渡到终点。
> 
> 基于物理的动画（Physics-based animation）：该种动画模仿真实世界的行为。例如，当你投掷一个球时，它落在哪里和何时取决于它被投掷的速度和离地面的距离。

### [Animations overview](https://flutter.dev/docs/development/ui/animations/overview)

+ 大部分 widget 通过接收一个 Animation 类型的对象实现动画效果，并从这个对象读取动画的当前值，以及监听这个对象获取变化的值

+ 每当动画的值发生更改时，动画将通知所有使用addListener添加的侦听器。通常，侦听动画的状态对象将在其侦听器回调中调用自身的setState，以通知widget系统它需要用动画的新值重建

+ 有两个小部件可以在动画更改值时帮助小部件重建：AnimatedWidget和AnimatedBuilder。第一个是AnimatedWidget，对于无状态的动画widget最有用。要使用AnimatedWidget，只需将其子类化并实现构建函数。第二个是AnimatedBuilder，对于希望将动画作为更大构建函数的一部分包含在内的更复杂的小部件非常有用。要使用AnimatedBuilder，只需构造小部件并向其传递一个builder函数

+ 要创建动画，请首先创建AnimationController。除了作为动画本身之外，AnimationController还允许您控制动画。例如，可以告诉控制器向前播放动画或停止动画。还可以投掷动画，该动画使用物理模拟（例如弹簧）来驱动动画

+ 创建动画控制器后，可以开始基于它构建其他动画。例如，可以创建一个反向动画，该反向动画镜像原始动画，但运行方向相反（例如，从1.0到0.0）。类似地，可以创建一个曲线动画，其值由曲线调整

### [Animations tutorial](https://flutter.dev/docs/development/ui/animations/tutorial)

### [Implicit Animations](https://flutter.dev/docs/development/ui/animations/implicit-animations)

### [Hero Animations](https://flutter.dev/docs/development/ui/animations/hero-animations)

### [Staggered Animations](https://flutter.dev/docs/development/ui/animations/staggered-animations)

## Advanced UI

### [Slivers](https://flutter.dev/docs/development/ui/advanced/slivers)

+ *nothing to note*

### [Gestures](https://flutter.dev/docs/development/ui/advanced/gestures)

+ Flutter 的手势系统包含两个层面：

> 第一层有原始指针事件，用于描述指针（例如触摸、鼠标和样式）在屏幕上的位置和移动
> 
> 第二层有描述由一个或多个指针动作组成的语义动作的手势

+ Pointers

> 指针表示用户与设备屏幕交互的原始数据。指针事件有四种类型:
> 
> PointerDownEvent : 指针已在特定位置与屏幕接触
> 
> PointerMoveEvent : 指针已从屏幕上的一个位置移动到另一个位置
> 
> PointerUpEvent : 指针已停止接触屏幕
> 
> PointerCancelEvent : 此指针的输入不再指向此应用程序
> 
> 在指针按下时，框架对应用程序进行命中测试，以确定指针在屏幕上接触的位置存在哪个widget
> 
> 然后，指针向下事件（以及该指针的后续事件）被调度到命中测试找到的最里面的widget
> 
> 从那里，事件在树上冒泡，并被分派到从最里面的widget到树根路径上的所有widget
> 
> 没有取消或停止进一步调度指针事件的机制
> 
> 要直接从widgets层监听指针事件，请使用Listener widget。不过，一般来说，可以考虑使用手势

+ Gestures

> 手势表示从多个单独指针事件（甚至可能是多个单独指针）识别的语义操作（例如，点击、拖动和缩放）。手势可以分派多个事件，对应于手势的生命周期（例如，拖动开始、拖动更新和拖动结束）
> 
> *Tap*
> 
> onTapDown : 可能导致点击的指针已在特定位置与屏幕接触
> 
> onTapUp : 触发点击的指针已在特定位置停止与屏幕接触
> 
> onTap : 先前触发onTapDown的指针也触发了onTapUp，最后导致了一个tap
> 
> onTapCancel : 先前触发onTapDown的指针不会导致点击
> 
> *Double tap*
> 
> onDoubleTap : 用户连续两次快速点击同一位置的屏幕
> 
> *Long press*
> 
> onLongPress : 指针在同一位置与屏幕保持长时间接触
> 
> *Vertical drag*
> 
> onVerticalDragStart : 指针已与屏幕接触，可能开始垂直移动
> 
> onVerticalDragUpdate : 与屏幕接触并垂直移动的指针已沿垂直方向移动
> 
> onVerticalDragEnd : 以前与屏幕接触并垂直移动的指针不再与屏幕接触，并在停止与屏幕接触时以特定速度移动
> 
> *Horizontal drag*
> 
> onHorizontalDragStart : 指针接触到屏幕，可能开始水平移动
> 
> onHorizontalDragUpdate : 与屏幕接触并水平移动的指针已在水平方向上移动
> 
> onHorizontalDragEnd : 以前与屏幕接触并水平移动的指针不再与屏幕接触，并在停止与屏幕接触时以特定速度移动
> 
> *Pan*
> 
> onPanStart : 指针已与屏幕接触，可能开始水平或垂直移动。如果设置了onHorizontalDragStart或onVerticalDragStart，则此回调将导致崩溃
> 
> onPanUpdate : 与屏幕接触并在垂直或水平方向上移动的指针。如果设置了onHorizontalDragUpdate或onVerticalDragUpdate，则此回调将导致崩溃
> 
> onPanEnd : 以前与屏幕接触的指针不再与屏幕接触，并且在停止与屏幕接触时以特定速度移动。如果设置了onHorizontalDragEnd或onVerticalDragEnd，则此回调将导致崩溃
> 

+ Adding gesture detection to widgets

> 使用 GestureDetector 来监听手势
> 
> Material 组件已能响应手势
> 

+ Gesture disambiguation(手势消歧)

> 在屏幕上的给定位置，可能有多个手势检测器。所有这些手势检测器都会在指针事件经过并试图识别特定的手势时监听指针事件流。GestureDetector widget根据其回调的非空性决定尝试识别哪些手势
> 
> 当屏幕上给定指针有多个手势识别器时，框架通过让每个识别器加入手势竞技场来消除用户想要的手势的歧义。手势竞技场使用以下规则确定哪个手势获胜：
> 
> *任何时候，识别器都可以宣布失败并离开竞技场。如果竞技场上只剩下一个识别器，那个识别器就是赢家*
> 
> *在任何时候，识别器都可以宣布胜利，这将导致它获胜，而其余的识别器都将失败*
> 
> 例如，当消除水平和垂直拖动的歧义时，两个识别器在收到指针向下事件时都会进入竞技场。识别器观察指针移动事件。如果用户水平移动指针超过一定数量的逻辑像素，水平识别器将宣布胜利，手势将解释为水平拖动。类似地，如果用户垂直移动超过一定数量的逻辑像素，则垂直识别器宣布胜利
> 
> 当只有水平（或垂直）拖动识别器时，手势竞技场是有益的。在这种情况下，竞技场中只有一个识别器，水平拖动被立即识别，这意味着水平移动的第一个像素可以被视为拖动，用户不需要等待进一步的手势消歧

## Stage managenment

### [Start thinking declaratively](https://flutter.dev/docs/development/data-and-backend/state-mgmt/declarative)

+ 在Flutter中，可以从头开始重建部分UI，而不是修改它
+ Flutter是陈述性的(declarative)。这意味着Flutter将构建其用户界面来反映应用程序的当前状态
+ 当应用程序的状态更改时（例如，用户在设置屏幕中翻转一个开关），您将更改状态，这将触发用户界面的重画。用户界面本身（如widget.setText）没有必要改变——你改变了状态，用户界面就从头开始重建

### [区分短暂状态和应用程序状态](https://flutter.dev/docs/development/data-and-backend/state-mgmt/ephemeral-vs-app)

+ 广义上讲，app状态包括app运行时内存中所有的信息。但有些状态又框架帮助处理，不需自己处理

+ 状态可以理解为 ： 为了在任何时候重建UI而需要的任何数据

+ 短暂状态（Ephemeral state）

> 短暂状态的例子 ： PageView 的当前页，BottomNavigationBar 的当前选中页
> 
> widget树的其他部分不需要访问这些状态，也不需要持久化

+ 应用程序状态（App state）

> 在应用的多个部分之间共享的状态，也称为共享状态
> 
> 举例：用户首选项、注册信息、社交应用中的通知、电商app中的购物车、新闻app中的文章已读、未读标志
> 
> 没有明确的通用规则来区分特定变量是短暂的还是应用程序状态。有时候，你得把一个重构成另一个。例如，您将从一些明显短暂的状态开始，但是随着应用程序功能的增长，它将需要移动到应用程序状态
> 

### [Simple app state management](https://flutter.dev/docs/development/data-and-backend/state-mgmt/simple)

+ 使用 Redux, Rx, hooks, provider 都可以实现状态管理
+ 在Flutter中，将状态保持在使用它的widget之上是有意义的
+ 当状态改变，相关的widget会消失并被新的widget替换，这就是所说的widget是不变的

+ ChangeNotifier

> ChangeNotifier向它的监听者提供notification
> 
> 对于 ChangeNotifier ，唯一特殊的是调用 notifyListeners()
> 
> 在模型更改时调用此方法，可能会更改应用程序的UI

+ ChangeNotifierProvider

> ChangeNotifierProvider 向它的后台提供 ChangeNotifier 实例
> 
> 如下，为App下级widget提供CartModel状态模型：

```
void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => CartModel(),
      child: MyApp(),
    ),
  );
}
```

> 可以使用 MultiProvider 提供多个状态对象

```
void main() {
  runApp(
    MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (context) => CartModel()),
        Provider(create: (context) => SomeOtherClass()),
      ],
      child: MyApp(),
    ),
  );
}
```

+ Consumer

> 可以通过 Consumer widget 使用上述定义的 CartModel

```
return Consumer<CartModel>(
  builder: (context, cart, child) {
    return Text("Total price: ${cart.totalPrice}");
  },
);
```

> Consumer 必须使用泛型来定义状态模型
> 
> Consumer widget 构造方法的唯一参数是 builder，builder 是一个函数，每当 ChangeNotifier 变换时将被调用
> 
> builder 有三个参数， context ： 每个builder参数都有； ChangeNotifier ：ChangeNotifier的实例；child ： 第三个参数是child，用于优化。如果您的使用者下面有一个大的widget子树，当模型改变时它不会改变，那么您可以构造它一次并通过构建器获得它 
> 
> 最好的做法是将消费者widget尽可能深入到树中。你不想仅仅因为某个地方的一些细节改变就重建大部分UI

+ Provider.of

```
Provider.of<CartModel>(context, listen: false).add(item);
```

> 在build方法中使用上述行不会导致调用notifyListeners时重新生成此widget

+ 为了使用provider，在 pubspec.yaml 中增加依赖 provider: ^3.0.0 ；这样在可以 import 'package:provider/provider.dart'

### [List of state management approaches](https://flutter.dev/docs/development/data-and-backend/state-mgmt/options)

## [Networking & http](https://flutter.dev/docs/development/data-and-backend/networking)

+ http包提供了发出http请求的最简单方法。这个包在Android、iOS和web上都支持

+ Android应用程序必须在Android清单（Android manifest.xml）中声明其对互联网的使用

```
<manifest xlmns:android...>
 ...
 <uses-permission android:name="android.permission.INTERNET" />
 <application ...
</manifest>
```

### [Fetch data from the internet](https://flutter.dev/docs/cookbook/networking/fetch-data)

+ Add the http package

> 要安装http包，将其添加到pubspec.yaml的dependencies部分

```
dependencies:
  http: <latest_version>
```

+ 导入http包

```
import 'package:http/http.dart' as http;
```

+ Make a network request

> 在本例中，使用http.get（）方法从JSONPlaceholder中获取一个示例帖子

```
Future<http.Response> fetchPost() {
  return http.get('https://jsonplaceholder.typicode.com/posts/1');
}
```

> Future是处理异步操作的核心Dart类。Future对象表示将来某个时间可用的潜在值或错误
> 
> http.Response类包含从成功的http调用接收的数据

+ Convert the response into a custom Dart object

> 使用原始 Future<http.Response> 不是很方便。为了简便，将http.Response转换为一个Dart对象
> 
> *Create a Post class*
> 
> 首先，创建一个Post类，其中包含来自网络请求的数据。它包括一个工厂构造函数，它从JSON创建Post

```
class Post {
  final int userId;
  final int id;
  final String title;
  final String body;

  Post({this.userId, this.id, this.title, this.body});

  factory Post.fromJson(Map<String, dynamic> json) {
    return Post(
      userId: json['userId'],
      id: json['id'],
      title: json['title'],
      body: json['body'],
    );
  }
}
```

> *Convert the http.Response to a Post*
> 
> 使用dart:Convert包将响应体转换为JSON映射
> 
> 如果服务器返回状态代码为200的“OK”响应，则使用fromJson（）factory方法将JSON映射转换为Post
> 
> 如果服务器返回意外响应，则抛出错误
> 

```
Future<Post> fetchPost() async {
  final response =
      await http.get('https://jsonplaceholder.typicode.com/posts/1');

  if (response.statusCode == 200) {
    // If server returns an OK response, parse the JSON.
    return Post.fromJson(json.decode(response.body));
  } else {
    // If that response was not OK, throw an error.
    throw Exception('Failed to load post');
  }
}
```

+ Fetch the data

> 在initState（）或didChangeDependencies（）方法中调用fetch方法
> 
> initState（）方法只调用一次，然后再也不调用
> 
> 如果您想选择重新加载API以响应 InheritedWidget 的更改，请将调用放入didChangeDependencies（）方法

```
class _MyAppState extends State<MyApp> {
  Future<Post> post;

  @override
  void initState() {
    super.initState();
    post = fetchPost();
  }
```

+ Display the data

> 要在屏幕上显示数据，请使用 FutureBuilder widget
> 
> FutureBuilder 使使用异步数据源变得容易

```
FutureBuilder<Post>(
  future: post,
  builder: (context, snapshot) {
    if (snapshot.hasData) {
      return Text(snapshot.data.title);
    } else if (snapshot.hasError) {
      return Text("${snapshot.error}");
    }

    // By default, show a loading spinner.
    return CircularProgressIndicator();
  },
);
```

+ 完整例子

```
import 'dart:async';
import 'dart:convert';

import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;

Future<Post> fetchPost() async {
  final response =
      await http.get('https://jsonplaceholder.typicode.com/posts/1');

  if (response.statusCode == 200) {
    // If the call to the server was successful, parse the JSON.
    return Post.fromJson(json.decode(response.body));
  } else {
    // If that call was not successful, throw an error.
    throw Exception('Failed to load post');
  }
}

class Post {
  final int userId;
  final int id;
  final String title;
  final String body;

  Post({this.userId, this.id, this.title, this.body});

  factory Post.fromJson(Map<String, dynamic> json) {
    return Post(
      userId: json['userId'],
      id: json['id'],
      title: json['title'],
      body: json['body'],
    );
  }
}

void main() => runApp(MyApp());

class MyApp extends StatefulWidget {
  MyApp({Key key}) : super(key: key);

  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
Future<Post> post;

  @override
  void initState() {
    super.initState();
    post = fetchPost();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Fetch Data Example',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        appBar: AppBar(
          title: Text('Fetch Data Example'),
        ),
        body: Center(
          child: FutureBuilder<Post>(
            future: post,
            builder: (context, snapshot) {
              if (snapshot.hasData) {
                return Text(snapshot.data.title);
              } else if (snapshot.hasError) {
                return Text("${snapshot.error}");
              }

              // By default, show a loading spinner.
              return CircularProgressIndicator();
            },
          ),
        ),
      ),
    );
  }
}
```

### [Make authenticated requests](https://flutter.dev/docs/cookbook/networking/authenticated-requests)

+ http包提供了一种向请求添加头的方便方法。或者，使用dart:io库中的HttpHeaders类

```
import 'dart:async';
import 'dart:convert';
import 'dart:io';

import 'package:http/http.dart' as http;

Future<Post> fetchPost() async {
  final response = await http.get(
    'https://jsonplaceholder.typicode.com/posts/1',
    headers: {HttpHeaders.authorizationHeader: "Basic your_api_token_here"},
  );
  final responseJson = json.decode(response.body);

  return Post.fromJson(responseJson);
}

class Post {
  final int userId;
  final int id;
  final String title;
  final String body;

  Post({this.userId, this.id, this.title, this.body});

  factory Post.fromJson(Map<String, dynamic> json) {
    return Post(
      userId: json['userId'],
      id: json['id'],
      title: json['title'],
      body: json['body'],
    );
  }
}
```

### [Work with WebSockets](https://flutter.dev/docs/cookbook/networking/web-sockets)


## [JSON and serialization](https://flutter.dev/docs/development/data-and-backend/json)

+ 两种使用JSON的策略

> 手动序列化
> 
> 使用代码生成的自动序列化
> 
> 不同的项目具有不同的复杂性和用例。对于较小的概念验证项目或快速原型，使用代码生成器可能会过分。对于具有更复杂的JSON模型的应用程序，手工编码可以很快变得冗长乏味、重复性很强，并且可以应用于许多小错误

+ 对较小的项目使用手动序列化

> 手动JSON解码是指在dart:convert中使用内置的JSON解码器。它涉及到将原始JSON字符串传递给jsonDecode（）函数，然后在结果 Map<string，dynamic> 中查找所需的值。它没有外部依赖项或特定的设置过程，对于概念的快速验证很有帮助
> 
> 当项目变大时，手动解码的性能不好。手工编写解码逻辑会变得很难管理并且容易出错。如果在访问不存在的JSON字段时键入了一个键值，则在运行时，代码会引发错误

+ 对大中型项目使用代码生成

> JSON序列化和代码生成意味着有一个外部库为您生成编码模板。在一些初始设置之后，运行一个从模型类生成代码的文件观察程序。例如，json_serializable 和 built_value 就是这类库
> 
> 这种方法对一个更大的项目很适用。不需要手工编写样板文件，在编译时会捕获访问JSON字段时的输入错误。代码生成的缺点是它需要一些初始设置。此外，生成的源文件可能会在项目导航器中产生视觉混乱

+ Flutter 中没有类似 GSON/Jackson/Moshi 的类库

> GSON/Jackson/Moshi 需要使用反射。由于反射使默认情况下所有代码都隐式使用，因此很难 tree shaking。这些工具无法知道运行时哪些部分未使用，因此冗余代码很难去除。使用反射时无法轻松优化应用程序大小
> 

+ Serializing JSON manually using dart:convert

> 调用 dart:convert 中的 jsonDecode() 解码JSON

```
Map<String, dynamic> user = jsonDecode(jsonString);

print('Howdy, ${user['name']}!');
print('We sent the verification link to ${user['email']}.');
```
> jsonDecode（）返回一个Map<String，dynamic>，这意味着直到运行时才知道值的类型。使用这种方法，将失去大多数静态类型语言特性：类型安全性、自动完成以及最重要的编译时异常。代码将立即变得更容易出错

+ Serializing JSON using code generation libraries

> 尽管还有其他可用的库，但本指南使用json_serializable，这是一个自动的源代码生成器，可以为您生成json序列化样板文件
> 
> 如何选择JSON_serializable和build_value ： json_serializable包允许您使用注解使常规类可序列化，而built_value包提供了一种更高级的方法来定义也可以序列化为json的不可变值类
> 
> *Setting up json_serializable in a project*
> 
> 要在项目中包含json_serializable，需要一个常规依赖项和两个dev依赖项。简言之，dev依赖项是应用程序源代码中未包含的依赖项，它们仅在开发环境中使用
> 
> pubspec.yaml 示例如下：

```
dependencies:
  # Your other regular dependencies here
  json_annotation: <latest_version>

dev_dependencies:
  # Your other dev_dependencies here
  build_runner: <latest_version>
  json_serializable: <latest_version>
```

> 在项目根文件夹中运行flutter pub get（或在编辑器中单击packages get），使这些新的依赖项在项目中可用
> 
> *Creating model classes the json_serializable way*
> 
> 下面演示如何将用户类转换为json_serializable类
> 

```
import 'package:json_annotation/json_annotation.dart';

/// This allows the `User` class to access private members in
/// the generated file. The value for this is *.g.dart, where
/// the star denotes the source file name.
part 'user.g.dart';

/// An annotation for the code generator to know that this class needs the
/// JSON serialization logic to be generated.
@JsonSerializable()

class User {
  User(this.name, this.email);

  String name;
  String email;

  /// A necessary factory constructor for creating a new User instance
  /// from a map. Pass the map to the generated `_$UserFromJson()` constructor.
  /// The constructor is named after the source class, in this case, User.
  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);

  /// `toJson` is the convention for a class to declare support for serialization
  /// to JSON. The implementation simply calls the private, generated
  /// helper method `_$UserToJson`.
  Map<String, dynamic> toJson() => _$UserToJson(this);
}
```

> 通过此设置，源代码生成器生成用于从JSON编码和解码name和email字段的代码
> 
> 如果需要，定制命名策略也很容易。例如，如果API返回带有snake_case的对象，并且希望在模型中使用lowerCamelCase，则可以使用带有name参数的@JsonKey注解

```
/// Tell json_serializable that "registration_date_millis" should be
/// mapped to this property.
@JsonKey(name: 'registration_date_millis')
final int registrationDateMillis;
```

> *Running the code generation utility*
> 
> 当第一次创建 json_serializable 类时，将得到类似的错误 : "Target of URI hasn't been generated:'u.g.dart'"
> 
> 这些错误完全正常，只是因为模型类生成的代码还不存在。要解决这个问题，请运行生成序列化样板的代码生成器
> 
> *One-time code generation*
> 
> 通过在项目根目录中运行 `flutter pub run build_runner build`，可以在需要时为模型生成JSON序列化代码。这将触发一次性生成，该生成将遍历源文件，选择相关的源文件，并为它们生成必要的序列化代码
> 
> *Generating code continuously*
> 
> 观察器使我们的源代码生成过程更加方便。它监视项目文件中的更改，并在需要时自动生成必要的文件。在项目根目录中运行 `flutter pub run build_runner watch` 启动观察程序
> 
> 可以安全地启动一次watcher并让它在后台运行

+ Consuming json_serializable models

> 要以 json_serializable 的方式解码JSON字符串，实际上不需要对前面的代码做任何更改

```
Map userMap = jsonDecode(jsonString);
var user = User.fromJson(userMap);
```

> 编码也是如此。调用API与以前相同

```
String json = jsonEncode(user);
```

> 使用json_serializable，您可以忘记用户类中的任何手动json序列化。源代码生成器创建一个名为user.g.dart的文件，该文件具有所有必要的序列化逻辑。您不再需要编写自动测试来确保序列化工作，现在库的职责是确保序列化工作正常

+ Generating code for nested classes

> Address 类定义如下：

```
import 'package:json_annotation/json_annotation.dart';
part 'address.g.dart';

@JsonSerializable()
class Address {
  String street;
  String city;

  Address(this.street, this.city);

  factory Address.fromJson(Map<String, dynamic> json) => _$AddressFromJson(json);
  Map<String, dynamic> toJson() => _$AddressToJson(this);
}
```

> 为了使 User 类能正常的嵌套 Address 类，为 User 的  @JsonSerializable() 传递 explicitToJson: true

```
import 'address.dart';
import 'package:json_annotation/json_annotation.dart';
part 'user.g.dart';

@JsonSerializable(explicitToJson: true)
class User {
  String firstName;
  Address address;

  User(this.firstName, this.address);

  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);
  Map<String, dynamic> toJson() => _$UserToJson(this);
}
```

## Accessibility & Internation­alizing

### [Accessibility](https://flutter.dev/docs/development/accessibility-and-localization/accessibility)

### [Internation­alizing Flutter apps](https://flutter.dev/docs/development/accessibility-and-localization/internationalization)

---
# [*Cookbook*](https://flutter.dev/docs/cookbook)

## Persistence

### [Persist data with SQLite](https://flutter.dev/docs/cookbook/persistence/sqlite)

+ Flutter 通过 sqflite 使用 SQLite

+ sqflite包提供与SQLite数据库交互的类和函数；path包提供了定义将数据库存储在磁盘上的位置的函数

```
dependencies:
  flutter:
    sdk: flutter
  sqflite:
  path:
```

```
import 'dart:async';

import 'package:path/path.dart';
import 'package:sqflite/sqflite.dart';
```

+ Define the Dog data model

```
class Dog {
  final int id;
  final String name;
  final int age;

  Dog({this.id, this.name, this.age});
}
```

+ Open the database

```
// Open the database and store the reference.
final Future<Database> database = openDatabase(
  // Set the path to the database. Note: Using the `join` function from the
  // `path` package is best practice to ensure the path is correctly
  // constructed for each platform.
  join(await getDatabasesPath(), 'doggie_database.db'),
);
```

+ Create the dogs table

```
final Future<Database> database = openDatabase(
  // Set the path to the database.
  join(await getDatabasesPath(), 'doggie_database.db'),
  // When the database is first created, create a table to store dogs.
  onCreate: (db, version) {
    // Run the CREATE TABLE statement on the database.
    return db.execute(
      "CREATE TABLE dogs(id INTEGER PRIMARY KEY, name TEXT, age INTEGER)",
    );
  },
  // Set the version. This executes the onCreate function and provides a
  // path to perform database upgrades and downgrades.
  version: 1,
);
```

+ Insert a Dog into the database

```
// Update the Dog class to include a `toMap` method.
class Dog {
  final int id;
  final String name;
  final int age;

  Dog({this.id, this.name, this.age});

  // Convert a Dog into a Map. The keys must correspond to the names of the
  // columns in the database.
  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'name': name,
      'age': age,
    };
  }
}

// Define a function that inserts dogs into the database
Future<void> insertDog(Dog dog) async {
  // Get a reference to the database.
  final Database db = await database;

  // Insert the Dog into the correct table. You might also specify the
  // `conflictAlgorithm` to use in case the same dog is inserted twice.
  //
  // In this case, replace any previous data.
  await db.insert(
    'dogs',
    dog.toMap(),
    conflictAlgorithm: ConflictAlgorithm.replace,
  );
}

// Create a Dog and add it to the dogs table.
final fido = Dog(
  id: 0,
  name: 'Fido',
  age: 35,
);

await insertDog(fido);
```

+ Retrieve the list of Dogs

```
// A method that retrieves all the dogs from the dogs table.
Future<List<Dog>> dogs() async {
  // Get a reference to the database.
  final Database db = await database;

  // Query the table for all The Dogs.
  final List<Map<String, dynamic>> maps = await db.query('dogs');

  // Convert the List<Map<String, dynamic> into a List<Dog>.
  return List.generate(maps.length, (i) {
    return Dog(
      id: maps[i]['id'],
      name: maps[i]['name'],
      age: maps[i]['age'],
    );
  });
}

// Now, use the method above to retrieve all the dogs.
print(await dogs()); // Prints a list that include Fido.
```

+ Update a Dog in the database

```
Future<void> updateDog(Dog dog) async {
  // Get a reference to the database.
  final db = await database;

  // Update the given Dog.
  await db.update(
    'dogs',
    dog.toMap(),
    // Ensure that the Dog has a matching id.
    where: "id = ?",
    // Pass the Dog's id as a whereArg to prevent SQL injection.
    whereArgs: [dog.id],
  );
}

// Update Fido's age.
await updateDog(Dog(
  id: 0,
  name: 'Fido',
  age: 42,
));

// Print the updated results.
print(await dogs()); // Prints Fido with age 42.
```

+ Delete a Dog from the database

```
Future<void> deleteDog(int id) async {
  // Get a reference to the database.
  final db = await database;

  // Remove the Dog from the Database.
  await db.delete(
    'dogs',
    // Use a `where` clause to delete a specific dog.
    where: "id = ?",
    // Pass the Dog's id as a whereArg to prevent SQL injection.
    whereArgs: [id],
  );
}
```

+ 完整例子

```
import 'dart:async';

import 'package:path/path.dart';
import 'package:sqflite/sqflite.dart';

void main() async {
  final database = openDatabase(
    // Set the path to the database. Note: Using the `join` function from the
    // `path` package is best practice to ensure the path is correctly
    // constructed for each platform.
    join(await getDatabasesPath(), 'doggie_database.db'),
    // When the database is first created, create a table to store dogs.
    onCreate: (db, version) {
      return db.execute(
        "CREATE TABLE dogs(id INTEGER PRIMARY KEY, name TEXT, age INTEGER)",
      );
    },
    // Set the version. This executes the onCreate function and provides a
    // path to perform database upgrades and downgrades.
    version: 1,
  );

  Future<void> insertDog(Dog dog) async {
    // Get a reference to the database.
    final Database db = await database;

    // Insert the Dog into the correct table. Also specify the
    // `conflictAlgorithm`. In this case, if the same dog is inserted
    // multiple times, it replaces the previous data.
    await db.insert(
      'dogs',
      dog.toMap(),
      conflictAlgorithm: ConflictAlgorithm.replace,
    );
  }

  Future<List<Dog>> dogs() async {
    // Get a reference to the database.
    final Database db = await database;

    // Query the table for all The Dogs.
    final List<Map<String, dynamic>> maps = await db.query('dogs');

    // Convert the List<Map<String, dynamic> into a List<Dog>.
    return List.generate(maps.length, (i) {
      return Dog(
        id: maps[i]['id'],
        name: maps[i]['name'],
        age: maps[i]['age'],
      );
    });
  }

  Future<void> updateDog(Dog dog) async {
    // Get a reference to the database.
    final db = await database;

    // Update the given Dog.
    await db.update(
      'dogs',
      dog.toMap(),
      // Ensure that the Dog has a matching id.
      where: "id = ?",
      // Pass the Dog's id as a whereArg to prevent SQL injection.
      whereArgs: [dog.id],
    );
  }

  Future<void> deleteDog(int id) async {
    // Get a reference to the database.
    final db = await database;

    // Remove the Dog from the database.
    await db.delete(
      'dogs',
      // Use a `where` clause to delete a specific dog.
      where: "id = ?",
      // Pass the Dog's id as a whereArg to prevent SQL injection.
      whereArgs: [id],
    );
  }

  var fido = Dog(
    id: 0,
    name: 'Fido',
    age: 35,
  );

  // Insert a dog into the database.
  await insertDog(fido);

  // Print the list of dogs (only Fido for now).
  print(await dogs());

  // Update Fido's age and save it to the database.
  fido = Dog(
    id: fido.id,
    name: fido.name,
    age: fido.age + 7,
  );
  await updateDog(fido);

  // Print Fido's updated information.
  print(await dogs());

  // Delete Fido from the database.
  await deleteDog(fido.id);

  // Print the list of dogs (empty).
  print(await dogs());
}

class Dog {
  final int id;
  final String name;
  final int age;

  Dog({this.id, this.name, this.age});

  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'name': name,
      'age': age,
    };
  }

  // Implement toString to make it easier to see information about
  // each dog when using the print statement.
  @override
  String toString() {
    return 'Dog{id: $id, name: $name, age: $age}';
  }
}
```

### [Read and write files](https://flutter.dev/docs/cookbook/persistence/reading-writing-files)

+ Find the correct local path

> path_provider插件提供了一种与平台无关的方式来访问设备文件系统中常用的位置。支持访问两种文件系统
> 
> *Temporary directory:* 系统可以随时清除的临时目录（缓存）。在iOS上，这对应于NSCachesDirectory。在Android上，这是getCacheDir（）返回的值
> 
> *Documents directory:* 应用程序存储只有它才能访问的文件的目录。只有删除应用程序时，系统才会清除目录。在iOS上，这对应于NSDocumentDirectory。在Android上，这是AppData目录
> 
> 可以找到文档目录的路径，如下所示:

```
Future<String> get _localPath async {
  final directory = await getApplicationDocumentsDirectory();

  return directory.path;
}
```

+ Create a reference to the file location

> 创建 dart:io 中的 File 对象：

```
Future<File> get _localFile async {
  final path = await _localPath;
  return File('$path/counter.txt');
}
```

+ Write data to the file

```
Future<File> writeCounter(int counter) async {
  final file = await _localFile;

  // Write the file.
  return file.writeAsString('$counter');
}
```

+ Read data from the file

```
Future<int> readCounter() async {
  try {
    final file = await _localFile;

    // Read the file.
    String contents = await file.readAsString();

    return int.parse(contents);
  } catch (e) {
    // If encountering an error, return 0.
    return 0;
  }
}
```

+ Testing

> 要测试与文件交互的代码，需要模拟对MethodChannel（与宿主平台通信的类）的调用。出于安全原因，您不能直接与设备上的文件系统交互，因此您可以与测试环境的文件系统交互
> 
> 要模拟方法调用，请在测试文件中提供setupAll（）函数。此函数在执行测试之前运行

```
setUpAll(() async {
  // Create a temporary directory.
  final directory = await Directory.systemTemp.createTemp();

  // Mock out the MethodChannel for the path_provider plugin.
  const MethodChannel('plugins.flutter.io/path_provider')
      .setMockMethodCallHandler((MethodCall methodCall) async {
    // If you're getting the apps documents directory, return the path to the
    // temp directory on the test environment instead.
    if (methodCall.method == 'getApplicationDocumentsDirectory') {
      return directory.path;
    }
    return null;
  });
});
```

+ 完整例子

```
import 'dart:async';
import 'dart:io';

import 'package:flutter/foundation.dart';
import 'package:flutter/material.dart';
import 'package:path_provider/path_provider.dart';

void main() {
  runApp(
    MaterialApp(
      title: 'Reading and Writing Files',
      home: FlutterDemo(storage: CounterStorage()),
    ),
  );
}

class CounterStorage {
  Future<String> get _localPath async {
    final directory = await getApplicationDocumentsDirectory();

    return directory.path;
  }

  Future<File> get _localFile async {
    final path = await _localPath;
    return File('$path/counter.txt');
  }

  Future<int> readCounter() async {
    try {
      final file = await _localFile;

      // Read the file
      String contents = await file.readAsString();

      return int.parse(contents);
    } catch (e) {
      // If encountering an error, return 0
      return 0;
    }
  }

  Future<File> writeCounter(int counter) async {
    final file = await _localFile;

    // Write the file
    return file.writeAsString('$counter');
  }
}

class FlutterDemo extends StatefulWidget {
  final CounterStorage storage;

  FlutterDemo({Key key, @required this.storage}) : super(key: key);

  @override
  _FlutterDemoState createState() => _FlutterDemoState();
}

class _FlutterDemoState extends State<FlutterDemo> {
  int _counter;

  @override
  void initState() {
    super.initState();
    widget.storage.readCounter().then((int value) {
      setState(() {
        _counter = value;
      });
    });
  }

  Future<File> _incrementCounter() {
    setState(() {
      _counter++;
    });

    // Write the variable as a string to the file.
    return widget.storage.writeCounter(_counter);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Reading and Writing Files')),
      body: Center(
        child: Text(
          'Button tapped $_counter time${_counter == 1 ? '' : 's'}.',
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}
```

### [Store key-value data on disk](https://flutter.dev/docs/cookbook/persistence/key-value)

+ 使用 shared_preferences 插件保存少量 key-values

> 通常，您必须编写本地平台集成，以便在iOS和Android上存储数据。幸运的是，shared_preferences插件可以用来在磁盘上保存键值数据。shared preferences插件在iOS上包装NSUserDefaults，在Android上包装SharedPreferences，为简单的数据提供持久的存储

+ Add the dependency

```
dependencies:
  flutter:
    sdk: flutter
  shared_preferences: "<newest version>"
```

+ Save data

> 要持久化数据，请使用SharedPreferences类提供的setter方法。Setter方法可用于各种原语类型，如setInt、setBool和setString
> 
> Setter方法做两件事：第一，同步更新内存中的键值对。然后，将数据持久化到磁盘
> 

```
// obtain shared preferences
final prefs = await SharedPreferences.getInstance();

// set value
prefs.setInt('counter', counter);
```

+ Read data

> 要读取数据，请使用SharedPreferences类提供的适当getter方法。每个setter都有一个对应的getter。例如，可以使用getInt、getBool和getString方法

```
final prefs = await SharedPreferences.getInstance();

// Try reading data from the counter key. If it doesn't exist, return 0.
final counter = prefs.getInt('counter') ?? 0;
```

+ Remove data

```
final prefs = await SharedPreferences.getInstance();

prefs.remove('counter');
```

+ shared preferences 的限制

> 只能使用基本类型：int、double、bool、string和stringList
> 
> 它不是用来存储大量数据的

+ Testing support

> 使用共 shared_preferences 测试持久化数据的代码是一个好主意。您可以通过模拟 shared_preferences 库使用的MethodChannel来完成此操作

```
const MethodChannel('plugins.flutter.io/shared_preferences')
  .setMockMethodCallHandler((MethodCall methodCall) async {
    if (methodCall.method == 'getAll') {
      return <String, dynamic>{}; // set initial values here if desired
    }
    return null;
  });
```

+ 完整例子

```
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of the application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Shared preferences demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Shared preferences demo'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  @override
  void initState() {
    super.initState();
    _loadCounter();
  }

  //Loading counter value on start
  _loadCounter() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    setState(() {
      _counter = (prefs.getInt('counter') ?? 0);
    });
  }

  //Incrementing counter after click
  _incrementCounter() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    setState(() {
      _counter = (prefs.getInt('counter') ?? 0) + 1;
      prefs.setInt('counter', _counter);
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.display1,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```

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
+ [Dart语法学习 -- *good 值得再学习*](https://www.jianshu.com/p/9e5f4c81cc7d)

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

