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

---
# flutter操作
## 查看Flutter SDK分支
+ flutter channel
+ flutter packages get获取项目所有的依赖包
+ flutter packages upgrade 获取项目所有依赖包的最新版本

## 升级Flutter SDK和依赖包
+ flutter upgrade

---
# 网上资源
+ [Flutter 官网 Docs](https://flutter.dev/docs)
+ [Flutter 中文网](https://flutterchina.club)
+ [书: Flutter实战](https://book.flutterchina.club)
+ [Flutter gallery](https://github.com/flutter/flutter/tree/master/examples/flutter_gallery)

---
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

+ flutter致力于支持那些想让他们的应用程序更容易访问的开发者：尽可能多的人可以使用，包括那些有残疾的人，比如失明或运动障碍的人

+ flutter 有三个组件支持易访问性

> Large fonts : 使用用户指定的字体大小呈现文本小部件
> 
> Screen readers : 交流有关UI内容的口头反馈
> 
> Sufficient contrast : 使用具有足够对比度的颜色呈现小部件

+ Inspecting Accessibility support

> *Android*
> 
> Install the Accessibility Scanner for Android
> 
> Enable the Accessibility Scanner from Android Settings > Accessibility > Accessibility Scanner > On
> 
> Navigate to the Accessibility Scanner ‘checkbox’ icon button to initiate a scan
> 
> *iOS*
> Open the iOS folder of your Flutter app in Xcode
> 
> Select a Simulator as the target, and click Run button
> 
> In Xcode, select Xcode > Open Developer Tools > Accessibility Inspector
> 
> In the Accessibility Inspector, select Inspection > Enable Point to Inspect, and then select the various user interface elements in running Flutter app to inspect their accessibility attributes
> 
> 
> In the Accessibility Inspector, select Audit in the toolbar, and then select Run Audio to get a report of potential issues

+ Large fonts

> Android和iOS都包含系统设置，用于配置应用程序使用的所需字体大小。在确定字体大小时，Flutter文本小部件会遵守此操作系统设置
> 
> 字体大小是根据操作系统设置通过Flutter自动计算的。但是，作为开发人员，您应该确保您的布局有足够的空间在字体大小增加时呈现其所有内容。例如，您可以在配置为使用最大字体设置的小屏幕设备上测试应用程序的所有部分

+ Screen readers

> 屏幕阅读器（TalkBack, VoiceOver 对讲、画外音）使视障用户能够获得关于屏幕内容的语音反馈
> 
> 打开设备上的VoiceOver或TalkBack并在应用程序中导航。如果遇到任何问题，请使用语义小部件自定义应用程序的可访问性体验

+ Sufficient contrast

> 充足的颜色对比度使文本和图像更易于阅读。在极端光线条件下（如在阳光直射下或在亮度较低的显示器上）观看设备上的界面时，充分的颜色对比度有助于帮助有各种视觉障碍的用户受益
> 
> 确保包含的任何图像具有足够的对比度
> 
> 在小部件上指定颜色时，请确保在前景和背景颜色选择之间使用足够的对比度

### [Internation­alizing Flutter apps](https://flutter.dev/docs/development/accessibility-and-localization/internationalization)

+ [Flutter-国际化适配终结者 - 好像不太管用](https://juejin.im/post/5c701379f265da2d9b5e196a#heading-1)

+ 建立一个国际化的应用程序：flutter_localizations 包

> 默认情况下，Flutter只提供英语本地化。要添加对其他语言的支持，应用程序必须指定其他MaterialApp属性，并包含一个名为flutter_localizations的单独包。截至2019年4月，该软件包支持大约52种语言。如果你想让你的应用在iOS上顺利运行，那么你还必须添加“flutter_cupertino_localizations”包
> 
> 要使用 flutter_localizations，请将包作为依赖项添加到pubspec.yaml文件中：

```
dependencies:
  flutter:
    sdk: flutter
  flutter_localizations:
    sdk: flutter
  flutter_cupertino_localizations: ^1.0.1
```

> 接下来，导入 flutter_localizations 库并为MaterialApp指定本地化 delegates 和 supportedLocales 属性：

```
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:flutter_cupertino_localizations/flutter_cupertino_localizations.dart';

MaterialApp(
 localizationsDelegates: [
   // ... app-specific localization delegate[s] here
   GlobalMaterialLocalizations.delegate,
   GlobalWidgetsLocalizations.delegate,
   GlobalCupertinoLocalizations.delegate,
 ],
 supportedLocales: [
    const Locale('en'), // English
    const Locale('he'), // Hebrew
    const Locale.fromSubtags(languageCode: 'zh'), // Chinese *See Advanced Locales below*
    // ... other locales the app supports
  ],
  // ...
)
```

> 基于WidgetsApp的应用程序类似，只是不需要GlobalMaterialLocalizations.delegate
> 
> 首选完整的Locale.fromSubtags构造函数，因为它支持脚本代码，尽管区域设置默认构造函数仍然完全有效
> 
> GlobalMaterialLocalizations.delegate 为 Material 组件库提供本地化字符串和其他值
> 
> GlobalWidgetsLocalizations.delegate 定义 widget 库的默认文字方向，或自左至右，或自右至左

+ Advanced locale definition

> 有些具有多个变体的语言需要一个以上的语言代码才能正确区分
> 
> 例如，完全区分中文的所有变体需要指定语言代码、脚本代码和国家代码。这是因为存在简化的和传统的脚本，以及在相同的脚本类型中写入字符的区域差异
> 
> 为了充分表达国家代码CN、TW和HK的所有中文变体，支持的地区列表应包括：

```
// Full Chinese support for CN, TW, and HK
supportedLocales: [
  const Locale.fromSubtags(languageCode: 'zh'), // generic Chinese 'zh'
  const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hans'), // generic simplified Chinese 'zh_Hans'
  const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hant'), // generic traditional Chinese 'zh_Hant'
  const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hans', countryCode: 'CN'), // 'zh_Hans_CN'
  const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hant', countryCode: 'TW'), // 'zh_Hant_TW'
  const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hant', countryCode: 'HK'), // 'zh_Hant_HK'
],
```

> 关于 zh_Hans 等参见 [HTML5中的lang属性，zh-CN还是zh-Hans？](https://www.cnblogs.com/cndavidwang/p/11790153.html)
> 
> 此明确的完整定义将确保您的应用程序能够区分并为这些国家/地区代码的所有组合提供完全细微差别的本地化内容
> 
> 如果未指定用户的首选区域设置，则将使用最接近的匹配，这可能包含与用户期望的不同
> 
> Flutter 只解析 supportedLocales 中定义的区域
> 
> Flutter为常用语言提供脚本代码区分的本地化内容

+ 跟踪区域设置 ： Locale 类和 Localizations widget

> Locale类用于标识用户的语言。移动设备支持为所有应用程序设置区域设置，通常通过系统设置菜单。国际化应用程序通过显示特定于区域设置的值来响应。例如，如果用户将设备的语言环境从英语切换到法语，则显示“Hello World”的文本小部件将用“Bonjour le monde”重新构建
> 
> Localizations widget 定义其子级的区域设置和子级所依赖的本地化资源。WidgetsApp小部件创建本地化小部件，并在系统的区域设置更改时重建它
> 
> 始终可以使用Localizations.localeOf（）查找应用程序的当前区域设置：

```
Locale myLocale = Localizations.localeOf(context);
```

+ Localizations widget 加载和检索本地化值集合的对象

> 用于加载和查找包含本地化值集合的对象
> 
> Apps使用 Localizations.of(context,type) 引用这些对象
> 
> 如果设备的区域设置发生更改，Localizations widget 会自动加载新区域设置的值，然后重新生成使用它的 widget。这是因为 Localizations 类似于 InheritedWidget

## Platform integation

### [Writing custom platform-specific code](https://flutter.dev/docs/development/platform-integration/platform-channels)

+ Flutter 使用一个灵活的系统，允许在 Android 平台上使用 Java 或 Kotlin 代码调用平台特定API，或者在 Objective-C 或 Swift 代码上调用 iOS

+ Flutter 平台特定的API支持不依赖于代码生成，而是依赖于灵活的消息传递方式

> 应用程序的 Flutter 部分通过 platform channel 向其主机（应用程序的iOS或Android部分）发送消息
> 
> 主机监听 platform channel，并接收消息。然后，它使用原生编程语言调用特定于平台的api，并将响应发送回客户端，即应用程序的Flutter部分

+ Architectural overview: platform channels

> 消息通过 platform channel 在客户端（UI）和主机（平台）之间传递。消息和响应是异步传递的，以确保用户界面保持响应
> 
> 在客户端，MethodChannel（API）支持发送与方法调用相对应的消息。在平台方面，Android上的MethodChannel（API）和iOS上的FlutterMethodChannel（API）支持接收方法调用和发送结果。这些类允许你用很少的“样板”代码开发一个平台插件
> 
> 如果需要，方法调用也可以反向发送，平台充当在Dart中实现的方法的客户端

+ Platform channel data types support and codecs

> 标准 platform channel 使用标准消息编解码器，该编解码器支持简单的类JSON值（如布尔值、数字、字符串、字节缓冲区、列表和映射）的高效二进制序列化。当发送和接收值时，将自动对这些值进行序列化和反序列化

+ Example: Calling platform-specific iOS and Android code using platform channels

> 下面的代码演示如何调用特定于平台的API来检索和显示当前电池电量。它使用Android BatteryManager API和iOS device.batteryLevel API，通过一条平台消息getBatteryLevel（）
> 
> 该示例将特定于平台的代码添加到主应用程序本身中。如果您希望为多个应用程序重用特定于平台的代码，则项目创建步骤略有不同，但平台通道代码仍以相同的方式编写
> 
> *Step 1: Create a new app project*
> 
> 在终端运行 ： flutter create batterylevel
> 
> 默认情况下，我们的模板支持使用Kotlin编写Android代码，或者使用Swift编写iOS代码。要使用Java或Objective-C，请使用-i和/或-a标志：

```
flutter create -i objc -a java batterylevel
```

> *Step 2: Create the Flutter platform client*
> 
> 应用程序的State类保存当前的应用程序状态。将其扩展以保持当前电池状态
> 
> 首先，构建 channel。使用MethodChannel和返回电池电量的单平台方法
> 
> 通道的客户端和主机端通过通道构造函数中传递的通道名称进行连接。单个应用程序中使用的所有通道名称都必须是唯一的；在通道名称前面加上唯一的“域前缀”，例如：samples.flutter.dev/battery

```
// main.dart

import 'dart:async';

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
...
class _MyHomePageState extends State<MyHomePage> {
  static const platform = const MethodChannel('samples.flutter.dev/battery');

  // Get battery level.
}
```

> 接下来，在 method channel 上调用一个方法，通过字符串标识符getBatteryLevel指定要调用的具体方法。例如，如果平台不支持平台API（例如在模拟器中运行时），则调用可能会失败，因此将invokeMethod调用包装在try catch语句中

```
// main.dart

// Get battery level.
String _batteryLevel = 'Unknown battery level.';

Future<void> _getBatteryLevel() async {
  String batteryLevel;
  try {
    final int result = await platform.invokeMethod('getBatteryLevel');
    batteryLevel = 'Battery level at $result % .';
  } on PlatformException catch (e) {
    batteryLevel = "Failed to get battery level: '${e.message}'.";
  }

  setState(() {
    _batteryLevel = batteryLevel;
  });
}
```

> 最后，将模板中的build方法替换为包含一个小用户界面，该界面以字符串形式显示电池状态，并包含一个刷新按钮

```
// main.dart

@override
Widget build(BuildContext context) {
  return Material(
    child: Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.spaceEvenly,
        children: [
          RaisedButton(
            child: Text('Get Battery Level'),
            onPressed: _getBatteryLevel,
          ),
          Text(_batteryLevel),
        ],
      ),
    ),
  );
}
```

> *Step 3: Add an Android platform-specific implementation*
> 
> 首先在Android Studio中打开Flutter应用程序的Android主机部分：
> 
> 1.打开 Android Studio
> 
> 2.选择菜单 File > Open…
> 
> 3.导航到保存Flutter应用程序的目录，并选择其中的android文件夹。单击“OK”
> 
> 4.在项目视图中打开java文件夹中的MainActivity.java文件
> 
> 接下来，创建MethodChannel并在configureFlutterEngine()方法内设置MethodCallHandler。确保使用与 Flutter 客户端相同的通道名称

```
// MainActivity.java

import androidx.annotation.NonNull;
import io.flutter.embedding.android.FlutterActivity;
import io.flutter.embedding.engine.FlutterEngine;
import io.flutter.plugin.common.MethodChannel;
import io.flutter.plugins.GeneratedPluginRegistrant;

public class MainActivity extends FlutterActivity {
  private static final String CHANNEL = "samples.flutter.dev/battery";

  @Override
  public void configureFlutterEngine(@NonNull FlutterEngine flutterEngine) {
    GeneratedPluginRegistrant.registerWith(flutterEngine);
    new MethodChannel(flutterEngine.getDartExecutor().getBinaryMessenger(), CHANNEL)
        .setMethodCallHandler(
          (call, result) -> {
            // Note: this method is invoked on the main thread.
            // TODO
          }
        );
  }
}
```

> 添加使用Android电池api检索电池电量的Android Java代码。这段代码与在原生Android应用程序中编写的代码完全相同
> 
> 首先，在文件顶部添加所需的导入：

```
// MainActivity.java

import android.content.ContextWrapper;
import android.content.Intent;
import android.content.IntentFilter;
import android.os.BatteryManager;
import android.os.Build.VERSION;
import android.os.Build.VERSION_CODES;
import android.os.Bundle;
```

> 然后在activity类的configureFlatterEngine（）方法下面添加以下作为新方法：

```
// MainActivity.java

private int getBatteryLevel() {
  int batteryLevel = -1;
  if (VERSION.SDK_INT >= VERSION_CODES.LOLLIPOP) {
    BatteryManager batteryManager = (BatteryManager) getSystemService(BATTERY_SERVICE);
    batteryLevel = batteryManager.getIntProperty(BatteryManager.BATTERY_PROPERTY_CAPACITY);
  } else {
    Intent intent = new ContextWrapper(getApplicationContext()).
        registerReceiver(null, new IntentFilter(Intent.ACTION_BATTERY_CHANGED));
    batteryLevel = (intent.getIntExtra(BatteryManager.EXTRA_LEVEL, -1) * 100) /
        intent.getIntExtra(BatteryManager.EXTRA_SCALE, -1);
  }

  return batteryLevel;
}
```

> 最后，完成前面添加的setMethodCallHandler（）方法。需要处理一个平台方法getBatteryLevel（），所以在call参数中测试它。这个平台方法的实现调用前一步编写的Android代码，并使用result参数返回成功和错误情况的响应。如果调用了未知方法，报告该方法
> 
> 删除以下代码：

```
// MainActivity.java

(call, result) -> {
  // Note: this method is invoked on the main thread.
  // TODO
}
```

> 并替换为以下内容：

```
// MainActivity.java

(call, result) -> {
  // Note: this method is invoked on the main thread.
  if (call.method.equals("getBatteryLevel")) {
    int batteryLevel = getBatteryLevel();

    if (batteryLevel != -1) {
      result.success(batteryLevel);
    } else {
      result.error("UNAVAILABLE", "Battery level not available.", null);
    }
  } else {
    result.notImplemented();
  }
}
```

> 现在应该可以在Android上运行这个应用了。如果使用Android模拟器，请在可从工具栏中的…按钮访问的扩展控制面板中设置电池电量

+ Step 4: Add an iOS platform-specific implementation

> 首先在Xcode中打开Flutter应用程序的iOS主机部分：
> 
> 1.打开 Xcode
> 
> 2.选择菜单项 File > Open…
> 
> 3.导航到保存Flutter应用程序的目录，并选择其中的ios文件夹。单击“OK”
> 
> 4.确保Xcode项目生成时没有错误
> 
> 5.打开文件AppDelegate.m，位于项目导航器的Runner>Runner下
> 
> 创建一个 FlutterMethodChannel 并在应用程序 didFinishLaunchingWithOptions: 方法中添加一个处理程序。确保使用与 Flutter 客户端相同的通道名称

```
// AppDelegate.m

#import <Flutter/Flutter.h>
#import "GeneratedPluginRegistrant.h"

@implementation AppDelegate
- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
  FlutterViewController* controller = (FlutterViewController*)self.window.rootViewController;

  FlutterMethodChannel* batteryChannel = [FlutterMethodChannel
                                          methodChannelWithName:@"samples.flutter.dev/battery"
                                          binaryMessenger:controller];

  [batteryChannel setMethodCallHandler:^(FlutterMethodCall* call, FlutterResult result) {
    // Note: this method is invoked on the UI thread.
    // TODO
  }];

  [GeneratedPluginRegistrant registerWithRegistry:self];
  return [super application:application didFinishLaunchingWithOptions:launchOptions];
}
```

> 接下来，添加iOS ObjectiveC代码，该代码使用iOS电池api来检索电池电量。此代码与原生iOS应用程序中编写的代码完全相同
> 
> 在AppDelegate类中的@end之前添加以下方法：

```
// AppDelegate.m

- (int)getBatteryLevel {
  UIDevice* device = UIDevice.currentDevice;
  device.batteryMonitoringEnabled = YES;
  if (device.batteryState == UIDeviceBatteryStateUnknown) {
    return -1;
  } else {
    return (int)(device.batteryLevel * 100);
  }
}
```

> 最后，完成前面添加的setMethodCallHandler（）方法。需要处理一个平台方法getBatteryLevel（），所以在call参数中测试它。此平台方法的实现调用在上一步中编写的iOS代码，并使用result参数返回成功和错误情况的响应。如果调用了未知方法，报告该方法

```
// AppDelegate.m

__weak typeof(self) weakSelf = self;
[batteryChannel setMethodCallHandler:^(FlutterMethodCall* call, FlutterResult result) {
  // Note: this method is invoked on the UI thread.
  if ([@"getBatteryLevel" isEqualToString:call.method]) {
    int batteryLevel = [weakSelf getBatteryLevel];

    if (batteryLevel == -1) {
      result([FlutterError errorWithCode:@"UNAVAILABLE"
                                 message:@"Battery info unavailable"
                                 details:nil]);
    } else {
      result(@(batteryLevel));
    }
  } else {
    result(FlutterMethodNotImplemented);
  }
}];
```

> 现在应该可以在iOS上运行这个应用了。如果使用iOS模拟器，请注意它不支持电池API，并且应用程序显示“电池信息不可用”

+ Separate platform-specific code from UI code

> 如果您希望在多个Flutter应用程序中使用特定于平台的代码，那么将代码分离到位于主应用程序外部目录中的平台插件中会很有用

+ Custom channels and codecs

> 除了上面提到的MethodChannel之外，您还可以使用更基本的BasicMessageChannel，它支持使用自定义消息编解码器的基本异步消息传递。您还可以使用专门的BinaryCodec、StringCodec和JSONMessageCodec类，或者创建自己的编解码器

+ Channels and Platform Threading

> 在编写平台端代码时，在平台主线程上调用所有的通道方法。在Android上，这个线程有时被称为“main thread”，但它在技术上被定义为 UI thread。用@UI thread注释需要在UI线程上运行的方法。在iOS上，这个线程被正式称为 main thread
> 
> *Jumping to the UI thread in Android*
> 
> 为了满足通道的UI线程需求，可能需要从后台线程跳到Android的UI线程来执行通道方法。在Android中，这是通过post（）对Android的UI线程循环器执行Runnable来实现的，这将导致Runnable在下一次机会时在主线程上执行
> 
> In Java:

```
new Handler(Looper.getMainLooper()).post(new Runnable() {
  @Override
  public void run() {
    // Call the desired channel message here.
  }
});
```

> In Kotlin:

```
Handler(Looper.getMainLooper()).post {
  // Call the desired channel message here.
}
```

> *Jumping to the main thread in iOS*
> 
> 为了满足通道的主线程需求，可能需要从后台线程跳到iOS的主线程来执行通道方法。在iOS中，这是通过在主调度队列上执行一个块来完成的：
> 
> In Objective-C:

```
dispatch_async(dispatch_get_main_queue(), ^{
  // Call the desired channel message here.
});
```

> In Swift:

```
DispatchQueue.main.async {
  // Call the desired channel message here.
}
```

## Packages & plugins

### [Using packages](https://flutter.dev/docs/development/packages-and-plugins/using-packages)

+ 一些第三方Packages

> [自定义导航/路由处理（FLURO）](https://pub.dev/packages/fluro)
> 
> [url_launcher](https://pub.dev/packages/url_launcher)
> 
> [battery](https://pub.dev/packages/battery)

+ 搜索 Packages

> 在 [pub.dev](pub.dev) 上搜索

+ 为 app 添加包依赖

> *以向 app 中添加 css_colors 包为例：*
> 
> 1、添加依赖：在 pubspec.yaml 中添加对 css_colors 的依赖
> 
> 2、安装：
> 
> 		终端 ： 运行 flutter pub get
> 
> 		Android Studio/IntelliJ：在pubspec.yaml顶部的操作功能区中单击Packages get
> 
> 		VS Code：单击位于pubspec.yaml顶部操作功能区右侧的“Get Packages”
> 
> 3、导入：在 Dart 代码中加入合适的 import 语句
> 
> 4、如果必要停止或重启 app ：如果包中包含特定于平台的代码（Android版的Java/Kotlin，iOS版的Swift/Objective-C），则必须将该代码内置到应用程序中。热重新加载和热重新启动只更新Dart代码，因此可能需要完全重新启动应用程序以避免在使用包时出现诸如MissingPluginException之类的错误
> 
> *可以在pub.dev上的任何包页面上找到Installing选项卡，它是这些步骤的方便参考*

+ 冲突解决

> 假设你想在一个应用程序中使用 some_package 和 another_package ，这两个包都依赖于 url_launcher ，但版本不同。这会引起潜在的冲突。避免这种情况的最佳方法是，包作者在指定依赖项时使用版本范围而不是特定版本

```
dependencies:
  url_launcher: ^0.4.2    # Good, any 0.4.x version where x >= 2 works.
  image_picker: '0.1.1'   # Not so good, only version 0.1.1 works.
```

> 如果 some_package 声明了上述依赖项，而 another_package 声明了兼容的 url_launcher 依赖项，如“0.4.5”或^0.4.0，则Pub会自动解决此问题。平台对Gradle模块和/或CocoaPods的依赖性以类似的方式解决
> 
> 即使 some_package 和 another_package 声明了 url_launcher 的不兼容版本，它们也可能以兼容的方式实际使用 url_launcher。在这种情况下，可以通过向应用程序的pubspec.yaml文件添加依赖项重写声明来解决冲突，强制使用特定版本

```
dependencies:
  some_package:
  another_package:
dependency_overrides:
  url_launcher: '0.4.3'
```

> 如果冲突的依赖项本身不是一个包，而是一个特定于Android的库（如guava），那么必须将依赖项重写声明添加到Gradle构建逻辑中
> 
> 要强制使用 guava v23.0，请对应用程序的android/build.gradle文件进行以下更改：

```
configurations.all {
    resolutionStrategy {
        force 'com.google.guava:guava:23.0-android'
    }
}
```

> CocoaPods目前不提供依赖覆盖功能

+ Package versions

> 所有包都有一个版本号，在包的pubspec.yaml文件中指定。包的当前版本显示在其名称旁边
> 
> 当一个包被添加到pubspec.yaml中时，缩写形式 `plugin1：` 意味着可以使用plugin1包的任何版本。要确保更新包时应用程序不会中断，请使用以下格式之一指定版本范围：
> 
> *范围限制：指定最小和最大版本*

```
dependencies:
  url_launcher: '>=0.1.2 <0.2.0'
```

> *使用 caret syntax 的范围限制*
> 
> 参见 [Package versioning](https://dart.dev/tools/pub/versioning)
> 
> 遵循语义版本 [Semantic Versioning 2.0.0-rc.1](https://semver.org/spec/v2.0.0-rc.1.html)

```
dependencies:
  collection: '^0.1.2'
```

+ 更新包依赖

> 添加包后首次运行 flutter pub get（Packages get in IntelliJ）时，flutter 将在 pubspec.lock Lockfile 中保存具体包版本。如果您或您团队中的其他开发人员运行flutter pub get，这将确保再次获得相同的版本
> 
> 要升级到包的新版本，例如使用包中的新功能，请运行flutter pub upgrade（IntelliJ中的 Upgrade dependencies ），以检索pubspec.yaml中指定的版本约束所允许的包的最高可用版本
> 
> *Lockfile*
> 
> 一个名为pubspec.lock的文件，指定包所依赖的每个即时和可传递依赖项的具体版本和其他标识信息
> 
> 与pubspec不同，pubspec只列出直接依赖项并允许版本范围，Lockfile 全面地将整个依赖关系图固定到包的特定版本。Lockfile 确保您可以重新创建应用程序使用的包的精确配置
> 
> 当您运行pub get、pub upgrade或pub degrade时，pub会自动为您生成 Lockfile。如果您的包是应用程序包，则通常会将其签入源代码管理。对于库包，通常不会

+ Dependencies on unpublished packages

> 即使没有在pub.dev上发布包，也可以使用包。对于私有插件或未准备好发布的包，可以使用其他依赖项选项
> 
> *Path dependency*
> 
> Flutter应用程序可以通过文件系统路径依赖插件。路径可以是相对路径，也可以是绝对路径。例如，要依赖位于应用程序同级应用目录中的插件 plugin1，请使用以下语法:

```
dependencies:
  plugin1:
    path: ../plugin1/
```

> *Git dependency*
> 
> 您还可以依赖于Git存储库中存储的包。如果包位于repo的根目录下，请使用以下语法:

```
dependencies:
  plugin1:
    git:
      url: git://github.com/flutter/plugin1.git
```

> *Git dependency on a package in a folder*
> 
> Pub假定包位于Git存储库的根目录中；如果不是这样，请使用path参数指定位置

```
dependencies:
  package1:
    git:
      url: git://github.com/flutter/packages.git
      path: packages/package1
```

> 最后，使用ref参数将依赖项固定到特定的git提交、分支或标记。更多细节，参见 [Package dependencies](https://dart.dev/tools/pub/dependencies)

+ 例子

> *Using the css_colors package*
> 
> css_colors 包为css颜色定义了颜色常量，因此在 flutter 框架需要颜色类型的地方使用这些常量
> 
> 1.创建新项目 cssdemo
> 
> 2.打开 pubspec.yaml，增加对 css-colors 的依赖：

```
dependencies:
  flutter:
    sdk: flutter
  css_colors: ^1.0.0
```

> 3.在终端运行 flutter pub get，或在 IntelliJ 点击 Packages get
> 
> 4.打开 lib/main.dart，按如下修改：

```
 import 'package:css_colors/css_colors.dart';
 import 'package:flutter/material.dart';

 void main() {
   runApp(MyApp());
 }

 class MyApp extends StatelessWidget {
   @override
   Widget build(BuildContext context) {
     return MaterialApp(
       home: DemoPage(),
     );
   }
 }

 class DemoPage extends StatelessWidget {
   @override
   Widget build(BuildContext context) {
     return Scaffold(body: Container(color: CSSColors.orange));
   }
 }
```

> 5.运行app，应用背景变为橘黄色
> 
> *Using the url_launcher package to launch the browser*
> 
> url_launcher插件包允许在移动平台上打开默认浏览器以显示给定的url，并且在Android和iOS上都被支持。该包演示了包可以包含特定于平台的代码，这些代码通常称为插件
> 
> 1.创建新项目 launchdemo
> 
> 2.打开 pubspec.yaml，添加对 url_launcher 的依赖：

```
dependencies:
  flutter:
    sdk: flutter
  url_launcher: ^0.4.1
```

> 3.在终端运行 flutter pub get，或在 IntelliJ 点击 Packages get
> 
> 4.打开 lib/main.dart，按如下修改：

```
 import 'package:flutter/material.dart';
 import 'package:url_launcher/url_launcher.dart';

 void main() {
   runApp(MyApp());
 }

 class MyApp extends StatelessWidget {
   @override
   Widget build(BuildContext context) {
     return MaterialApp(
       home: DemoPage(),
     );
   }
 }

 class DemoPage extends StatelessWidget {
   launchURL() {
     launch('https://flutter.dev');
   }

   @override
   Widget build(BuildContext context) {
     return Scaffold(
       body: Center(
         child: RaisedButton(
           onPressed: launchURL,
           child: Text('Show Flutter homepage'),
         ),
       ),
     );
   }
 }
```

> 运行应用程序（或者停止并重新启动它，如果它在添加插件之前已经在运行）。点击显示 Flutter 主页。您应该会看到设备上打开的默认浏览器，显示了 Flutter 主页

### [Developing packages & plugins](https://flutter.dev/docs/development/packages-and-plugins/developing-packages)

+ Package introduction

> Package 包允许创建模块化代码，这些代码可以很容易地共享
> 
> *最小的 Package 包括:*
> 
> pubspec.yaml文件：声明包名称、版本、作者等的元数据文件
> 
> 一个lib目录，包含包中的公共代码，至少是一个<package name>.dart文件

+ Package types

> *Dart packages*
> 
> 用Dart编写的通用包，例如path包。其中一些可能包含特定于 Flutter 的功能，因此依赖于 Flutter 框架，将其仅限于 Flutter 使用，例如fluro包
> 
> *Plugin packages*
> 
> 一个专门的Dart包，其中包含一个用Dart代码编写的API，该API与Android（使用Java或Kotlin）和/或iOS（使用ObjC或Swift）的特定平台实现相结合。一个具体的例子是 battery 插件包

+ Developing Dart packages

> *Step 1: Create the package*

```
flutter create --template=package hello
```

> 这将在hello/文件夹中创建包含以下专门内容的包项目：
> 
> `lib/hello.dart` : 包的 Dart 代码
> 
> `test/hello_test.dart` : 包的单元测试
> 
> *Step 2: Implement the package*
> 
> 对于纯Dart包，只需在主lib/<package name>.Dart文件或lib目录中的几个文件中添加功能即可
> 
> 要测试包，请在测试目录中添加单元测试

+ Developing plugin packages

> 如果要开发调用平台特定api的包，则需要开发插件包。插件包是Dart包的一个专门版本，除了上面描述的内容外，它还包含为Android（Java或Kotlin代码）、iOS（Objective-C或Swift代码）或两者编写的特定于平台的实现。API使用 platform channels 连接到特定于平台的实现
> 
> *Step 1: Create the package*

```
flutter create --org com.example --template=plugin hello
```

> 这将在hello/文件夹中创建一个插件项目，其中包含以下特定内容:
> 
> `lib/hello.dart` : 插件的 Dart API
> 
> `android/src/main/java/com/example/​hello/HelloPlugin.kt` : 插件API的 Android 实现
> 
> `ios/Classes/HelloPlugin.m` : 插件API的 IOS 实现
> 
> `example/` : 一个依赖于本插件的Flutter应用程序，演示了如何使用它
> 
> 默认情况下，插件项目对iOS代码使用Swift，对Android代码使用Kotlin。如果您喜欢Objective-C或Java，可以使用-i指定iOS语言和/或使用-a指定Android语言

```
flutter create --template=plugin -i objc -a java hello
```

> *Step 2: Implement the package*
> 
> 由于插件包包含用多种编程语言编写的多个平台的代码，因此需要一些特定的步骤来确保流畅的体验
> 
> *Step 2a: Define the package API (.dart)*
> 
> 插件包的API在Dart代码中定义。在你最喜欢的 Flutter 编辑器中打开主hello/文件夹。找到文件lib/hello.dart
> 
> *Step 2b: Add Android platform code (.java/.kt)*
> 
> 推荐使用 Android Studio 编辑 Android 代码
> 
> 在Android Studio中编辑Android平台代码之前，首先确保代码至少已经编译过一次（换句话说，从IDE/编辑器运行示例应用程序，或者在终端中执行cd hello/example；flutter build apk)
> 
> 下一步：
> 
> 1.打开 Android Studio
> 
> 2.在 ‘Welcome to Android Studio’ 对话框选择 ‘Import project’，或者打开菜单 ‘File > New > Import Project…’，选择 hello/example/android/build.gradle
> 
> 3.在 ‘Gradle Sync’ 对话框，选择  ‘OK’
> 
> 4.在 ‘Android Gradle Plugin Update’ 对话框，选择 ‘Don’t remind me again for this project’
> 
> 插件的Android平台代码位于hello/java/com.example.hello/hello plugin
> 
> 可以通过按  ▶  按钮从Android Studio运行示例应用程序
> 
> *Step 2c: Add iOS platform code (.h+.m/.swift)*
> 
> 推荐使用 Xcode 编辑 IOS 代码
> 
> 在Xcode中编辑iOS平台代码之前，首先确保代码至少已生成一次（即，从IDE/编辑器运行示例应用程序，或在终端中执行cd hello/example；flutter build ios --no-codesign）
> 
> 下一步：
> 
> 1.打开 Xcode
> 
> 2.打开 ‘File > Open’，选择 hello/example/ios/Runner.xcworkspace
> 
> 插件的iOS平台代码位于Pods/Development Pods/hello/Classes/项目导航器中
> 
> 可以通过按  ▶  按钮运行
> 
> *Step 2d: Connect the API and the platform code*
> 
> 最后，您需要将用Dart代码编写的API与特定于平台的实现连接起来。这是通过 platform channels 完成的。参见 [Writing custom platform-specific code](https://flutter.dev/docs/development/platform-integration/platform-channels)

+ Specifying a plugin’s supported platforms

> 在flutter 1.10及更高版本中，插件可以通过在pubspec.yaml文件的 platforms map 中添加 key 来指定它们支持的平台。例如，下面是“hello”插件的flutter:map

```
flutter:
  plugin:
    platforms:
      android:
        package: com.example.hello
        pluginClass: HelloPlugin
      ios:
        pluginClass: HelloPlugin

environment:
  sdk: ">=2.1.0 <3.0.0"
  # Flutter versions prior to 1.10 did not support the flutter.plugin.platforms map.
  flutter: ">=1.10.0 <2.0.0"
```

> 当为更多平台添加插件实现时，platforms map 应相应更新，例如支持Android、iOS、macOS和Flutter Web的hello插件的 platforms map 如下：

```
flutter:
  plugin:
    platforms:
      android:
        package: com.example.hello
        pluginClass: HelloPlugin
      ios:
        pluginClass: HelloPlugin
      macos:
        pluginClass: HelloPlugin
      web:
        pluginClass: HelloPlugin
        fileName: hello_web.dart

environment:
  sdk: ">=2.1.0 <3.0.0"
  # Flutter versions prior to 1.10 did not support the flutter.plugin.platforms map.
  flutter: ">=1.10.0 <2.0.0"
```

+ Adding documentation

> 建议在所有软件包中添加以下文档：
> 
> 1.介绍包的README.md文件
> 
> 2.记录每个版本中更改的CHANGELOG.md文件
> 
> 3.包含软件包授权条款的许可文件
> 
> 4.所有公共API的API文档

+ API documentation

> 发布包时，API文档将自动生成并发布到dartdocs.org
> 
> 如果希望在本地生成API文档，请使用以下命令：
> 
> 1.将目录更改为包的位置：
> 
> cd ~/dev/mypackage
> 
> 2.告诉文档工具Flutter SDK的位置（更改以反映您放置它的位置）：
> 
> export FLUTTER_ROOT=~/dev/flutter (on macOS or Linux)
> 
> set FLUTTER_ROOT=~/dev/flutter (on Windows)
> 
> 3.运行dartdoc工具（作为Flutter SDK的一部分提供）：
> 
> $FLUTTER_ROOT/bin/cache/dart-sdk/bin/dartdoc (on macOS or Linux)
> 
> %FLUTTER_ROOT%\bin\cache\dart-sdk\bin\dartdoc (on Windows)

+ Adding licenses to the LICENSE file

> 每个许可证文件中的单个许可证应在一行上单独用80个连字符分隔
> 
> 如果许可证文件包含多个组件许可证，则每个组件许可证必须以组件许可证适用的包的名称开头，每个包的名称在其自己的行上，并且包名称列表与实际许可证文本之间用空行分隔。（包不需要与发布包的名称匹配。例如，一个包本身可能包含来自多个第三方源的代码，并且可能需要为每个源包含一个许可证。）
> 
> 正确做法：

```
package_1

<some license text>

--------------------------------------------------------------------------------
package_2

<some license text>
```

> 正确做法：

```
package_1

<some license text>

--------------------------------------------------------------------------------
package_1
package_2

<some license text>
```

> 错误做法：

```
<some license text>

--------------------------------------------------------------------------------
<some license text>
```

> 错误做法：

```
package_1

<some license text>
--------------------------------------------------------------------------------
<some license text>
```

+ Publishing packages

> 一旦实现了一个包，就可以在pub.dev上发布它，这样其他开发人员就可以轻松地使用它
> 
> 发布之前，请确保查看pubspec.yaml、README.md和CHANGELOG.md文件，以确保其内容完整且正确。另外，为了提高您的软件包的质量和可用性，请考虑包含以下项目
> 
> 不同的代码使用示例
> 
> 屏幕截图、动画gif或视频
> 
> 指向相应代码库的链接
> 
> 接下来，运行dry run命令，查看是否所有内容都通过了分析：

```
flutter pub publish --dry-run
```

> 最后，运行实际的发布命令：

```
flutter pub publish
```

+ Handling package interdependencies

> 如果开发的包hello依赖于另一个包公开的Dart API，则需要将该包添加到pubspec.yaml文件的依赖项部分。下面的代码使url_launcher插件的Dart API对hello可用(在hello/pubspec.yaml里)

```
dependencies:
  url_launcher: ^0.4.2
```

> 现在可以导入'package:url_launcher/url_launcher.dart'并在hello的dart代码中launch（someUrl）,这与在Flutter应用程序或任何其他Dart项目中包含包的方式没有区别
> 
> 但是，如果hello碰巧是一个插件包，其平台特定的代码需要访问由 url_launcher 公开的平台特定的api，则还需要向平台特定的构建文件添加适当的依赖关系声明
> 
> *Android* 修改 hello/android/build.gradle

```
android {
    // lines skipped
    dependencies {
        provided rootProject.findProject(":url_launcher")
    }
}
```

> 现在可以导入io.flutter.plugins.urllauncher.UrlLauncherPlugin并访问源代码hello/android/src中的UrlLauncherPlugin类
> 
> *iOS* 修改 hello/ios/hello.podspec

```
Pod::Spec.new do |s|
  # lines skipped
  s.dependency 'url_launcher'
```

> 现在可以导入“UrlLauncherPlugin.h”并访问源代码hello/ios/Classes中的UrlLauncherPlugin类

### [Flutter Favorite program](https://flutter.dev/docs/development/packages-and-plugins/favorites)

+ Flutter Favorite 程序的目标是识别在构建应用程序时应该首先考虑的包和插件。这并不能保证质量或适合您的特定情况，您应该始终为您的项目执行您自己的包和插件评估

+ Metrics

> Flutter Favorite 软件包已经通过了高质量标准，使用以下指标:
> 
> [Overall package score](https://pub.dev/help)
> 
> 许可证，包括（但不限于）Apache、art、BSD、CC BY、MIT、MS-PL和W3C
> 
> GitHub version标记与pub.dev中的当前版本匹配，因此您可以确切地看到包中的源码
> 
> 功能完整且未标记为不完整（例如，带有“beta”或“正在构建”等标签）
> 
> Verified publisher
> 
> 在概述、文档、示例/示例代码和API质量方面的一般可用性
> 
> 在CPU和内存使用方面的良好运行时行为
> 
> 高质量依赖项

+ Flutter 生态委员会

> Flutter 生态系统委员会（FEC）由 Flutter 团队成员和遍布其生态系统的社区成员组成。他们的工作之一是决定一个包什么时候符合质量标准，成为 Flutter Favorite
> 
> 如果你想推荐一个软件包或插件作为未来 Flutter Favorite ，或者想引起委员会的注意，给委员会主席发一封邮件

+ Flutter Favorite usage guidelines

> Flutter Favorite 软件包将由Flutter团队在pub.dev上贴上这样的标签。如果您拥有一个已被指定为Flutter Favorite 的软件包，则必须遵守以下准则：
> 
> Flutter Favorite包的作者可以将 Flutter Favorite 徽标放在包的GitHub自述文件、包的pub.dev Overview选项卡和与该包相关的帖子相关的社交媒体上
> 
> 我们鼓励您在社交媒体中使用 `#FlutterFavorite` 标签
> 
> 当使用 Flutter Favorite 标志时，作者必须链接到 Flutter Favorite 的登录页，以提供指定的上下文
> 
> 如果一个Flutter Favorite包丢失了Flutter Favorite状态，将通知作者，此时作者必须立即从受影响的包中删除“Flutter Favorite”和Flutter Favorite徽标的所有用途
> 
> 不要以任何方式更改、扭曲或修改 Flutter Favorite 徽标，包括显示带有颜色变化或未经批准的视觉元素的徽标
> 
> 不要以误导、不公平、诽谤、侵权、诽谤、诋毁、淫秽或其他对谷歌不利的方式显示 Flutter Favorite 徽标

+ What’s next

> 你应该期待 Flutter Favorite 软件包列表会随着生态系统的不断发展而不断增长和变化。委员会将继续与软件包作者合作，以提高质量，并考虑生态系统中其他可能从 Flutter Favorite 程序中受益的领域，如工具、咨询公司和大量Flutter贡献者
> 
> 随着Flutter生态系统的发展，我们将着眼于扩展指标集，其中可能包括以下内容：
> 
> 使用新的pubspec.yaml格式，明确指出支持哪些平台
> 
> 支持最新稳定版本的 Flutter
> 
> 支持AndroidX
> 
> 支持多种平台，如web、macOS、Windows、Linux等
> 
> 集成和单元测试覆盖

+ Flutter Favorites

> [可以在pub.dev上看到 Flutter Favorites 完整列表](https://pub.dev/flutter/favorites)

### [Background processes](https://flutter.dev/docs/development/packages-and-plugins/background-processes)

> 即使您的应用程序不是当前活动的应用程序，您是否希望在后台执行Dart代码？也许你想实现一个监视时间或捕捉相机运动的过程。在Flutter中，可以在后台执行Dart代码
> 
> 此功能的机制包括设置 isolate。isolate 是Dart的多线程模型，尽管 isolate 不同于传统线程，因为它不与主程序共享内存。您将使用回调和回调分派器为后台执行设置 isolate
> 
> 有关更多信息和使用Dart代码后台执行的地理围栏示例，请参阅Flutter插件和地理围栏在后台执行Dart，这是Flutter发布在Medium上的一篇文章。在本文的最后，您将找到示例代码的链接，以及Dart、iOS和Android的相关文档

### [Supporting the new Android plugins APIs](https://flutter.dev/docs/development/packages-and-plugins/plugin-api-migration)

## Add Flutter to existing app

### [Add Flutter to existing app Introduction](https://flutter.dev/docs/development/add-to-app)

+ Flutter 可以作为一个库或模块，被集成到已有的应用程序中。然后，可以将该模块导入到Android或iOS（当前支持的平台）应用程序中，在Flutter中呈现应用程序UI的一部分。或者，只是为了运行共享的Dart逻辑

+ 从 Flutter v1.12 起，支持在每一个app中运行一个全屏的 Flutter 实例，但有下述限制：

> 运行多个 Flutter 实例或在部分屏幕视图中运行可能具有未定义的行为
> 
> 在后台模式下运行 Flutter 的功能尚在开发中
> 
> 不支持将Flutter库打包到另一个可共享库或将多个Flutter库打包到应用程序中

+ Add to Android applications

> 通过在Gradle脚本中添加Flutter SDK钩子自动构建和导入Flutter模块
> 
> 将Flutter模块构建到一个通用的Android存档（AAR）中，以集成到您自己的构建系统中，并与AndroidX实现更好的Jetifier互操作性
> 
> Android Studio Android/Flutter协同编辑和模块创建/导入向导
> 
> 支持Java和Kotlin主机应用程序
> 
> Flutter 模块可以使用 Flutter 插件与平台交互。Android插件应该迁移到 V2 插件api中，以获得最佳的应用程序正确性。从Flutter v1.12开始，Flutter 团队和 FlutterFire 维护的大多数插件都已迁移
> 
> 通过使用来自IDEs的Flutter attach或命令行连接到包含Flutter的应用程序，支持Flutter调试和状态热重新加载

+ Add to iOS applications

> 通过向CocoaPods和Xcode构建阶段添加Flutter SDK钩子，自动构建并导入Flutter模块
> 
> 将 Flutter 模块构建到一个通用的iOS框架中，以便集成到您自己的构建系统中
> 
> 支持Objective-C和Swift主机应用程序
> 
> Flutter 模块可以使用 Flutter 插件与平台交互
> 
> 通过使用来自IDEs的Flutter attach或命令行连接到包含Flutter的应用程序，支持Flutter调试和状态热重新加载

### Adding to an Android app

#### [Integrate a Flutter module into your Android project](https://flutter.dev/docs/development/add-to-app/android/project-setup)

+ Flutter 可以嵌入到现有的Android应用程序中，作为源代码 Gradle 子项目或AARs

+ 集成流程可以使用Android Studio IDE和Flutter插件完成，也可以手动完成

+ 现有的Android应用程序可能支持MIPS或 x86/x86_64 等架构。Flutter目前只支持为armeabi-v7a和arm64-v8a构建提前（AOT）编译的库

+ Using Android Studio

> Android Studio IDE是一种自动集成Flutter模块的便捷方式。使用Android Studio，可以在同一个项目中同时编辑Android代码和Flutter代码。也可以使用 IntelliJ Flutter 插件功能，比如Dart代码补全、热重新加载和widget检查器
> 
> Android Studio的 Add-to-app 流程仅在Android Studio 3.6 加上版本42+的Flutter IntelliJ插件上受支持。Android Studio集成也只支持使用源代码Gradle子项目进行集成，而不支持使用AARs
> 
> 使用 File > New > New Module... 在现有Android项目中的 Android Studio 菜单中，可以创建一个新的 Flutter 模块来集成，或者选择先前创建的现有 Flutter 模块
> 
> 如果创建新模块，可以使用向导选择模块名称、位置等
> 
> Android Studio插件会自动配置 Android 项目，将 Flutter 模块添加为依赖项，为应用程序准备好构建
> 
> 要查看IDE插件自动对Android项目所做的更改，请考虑在执行其他步骤之前使用版本控制工具检查变更
> 
> 默认情况下，项目的  Project pane 可能显示“Android”视图。如果在 Project pane 中看不到新的Flutter文件，请确保将  Project pane 设置为显示“项目文件”，其中显示所有文件而不进行筛选

+ Manual integration

> 为了将 Flutter 模块与现有的Android应用程序手动集成，而不使用 Android Studio 的 Flutter 插件，请遵循以下步骤：
> 
> *Create a Flutter module*
> 
> 假设你在 some/path/MyApp 上有一个现有的Android应用程序，你希望你的 Flutter 项目作为兄弟姐妹：

```
$ cd some/path/
$ flutter create -t module --org com.example my_flutter
```

+ Java 8 requirement

> Flutter Android引擎使用Java 8特性
> 
> 在尝试将 Flutter 模块项目连接到宿主Android应用程序之前，请确保宿主Android应用程序的 build.gradle 文件在 Android{} 块中声明以下源代码兼容性，例如：

```
// MyApp/app/build.gradle

android {
  //...
  compileOptions {
    sourceCompatibility 1.8
    targetCompatibility 1.8
  }
}
```

> *Add the Flutter module as a dependency*
> 
> 接下来，将 Flutter 模块作为 Gradle 现有应用程序的依赖项添加。实现这一目标有两种方法。AAR 机制创建通用的 Android AARs 作为中介来打包 Flutter 模块。采用这种方式的优点是，下游应用程序开发者不用安装 Flutter SDK；缺点是，如果需要经常构建，会增加一个构建步骤
> 
> 源代码子项目机制是一个方便的 one-click 构建过程，但需要Flutter SDK。这是Android Studio IDE插件使用的机制
> 
> *Option A - Depend on the Android Archive (AAR)*
> 
> 此选项将 Flutter 库打包为一个由AARs和POMs构件组成的通用本地Maven存储库。此选项允许您的团队在不安装Flutter SDK的情况下构建宿主应用程序。然后，您可以从本地或远程存储库分发工件
> 
> 假设您在 some/path/my_flutter 构建了 Flutter 模块，然后运行：

```
$ cd some/path/my_flutter
$ flutter build aar
```

> 更具体地说，该命令创建包含下述文件的本地存储库：

```
build/host/outputs/repo
└── com
    └── example
        └── my_flutter
            ├── flutter_release
            │   ├── 1.0
            │   │   ├── flutter_release-1.0.aar
            │   │   ├── flutter_release-1.0.aar.md5
            │   │   ├── flutter_release-1.0.aar.sha1
            │   │   ├── flutter_release-1.0.pom
            │   │   ├── flutter_release-1.0.pom.md5
            │   │   └── flutter_release-1.0.pom.sha1
            │   ├── maven-metadata.xml
            │   ├── maven-metadata.xml.md5
            │   └── maven-metadata.xml.sha1
            ├── flutter_profile
            │   ├── ...
            └── flutter_debug
                └── ...
```

> 要依赖AAR，宿主应用程序必须能够找到这些文件。为此，请在宿主应用程序中编辑app/build.gradle，例如它包含本地存储库和依赖项：

```
// MyApp/app/build.gradle

android {
  // ...
}

repositories {
  maven {
    url 'some/path/my_flutter/build/host/outputs/repo'
    // This is relative to the location of the build.gradle file
    // if using a relative path.
  }
  maven {
    url 'http://download.flutter.io'
  }
}

dependencies {
  // ...
  debugImplementation 'com.example.flutter_module:flutter_debug:1.0'
  profileImplementation 'com.example.flutter_module:flutter_profile:1.0'
  releaseImplementation 'com.example.flutter_module:flutter_release:1.0'
}
```

> 还可以使用 Build > Flutter > Build AAR 菜单在 Android Studio中 为Flutter模块构建 AAR
> 
> *Option B - Depend on the module’s source code*
> 
> 本方法为您的 Android 项目和 Flutter 项目启用一步构建。当同时处理这两个部分并快速迭代时，此方法非常方便，但是您的团队必须安装Flutter SDK来构建宿主应用程序
> 
> 将 Flutter 模块作为子项目包含在宿主应用程序的 settings.gradle 中:

```
// MyApp/settings.gradle

include ':app'                                     // assumed existing content
setBinding(new Binding([gradle: this]))                                 // new
evaluate(new File(                                                      // new
  settingsDir.parentFile,                                               // new
  'my_flutter/.android/include_flutter.groovy'                          // new
))                                                                      // new
```

> 假设 my_flutter 是 MyApp 的兄弟
> 
> 绑定和脚本评估允许Flutter模块在设置的评估上下文中包含自身（as:Flutter）和该模块使用的任何Flutter插件（as:package_info、：video_player等）
> 
> 在应用中引入对 Flutter 模块的实现依赖：

```
// MyApp/app/build.gradle

dependencies {
  implementation project(':flutter')
}
```

#### [Adding a Flutter screen to an Android app](https://flutter.dev/docs/development/add-to-app/android/add-flutter-screen)

+ 本指南介绍如何在现有 Android 应用程序中添加单个 Flutter 屏幕。 Flutter 屏幕可以添加为普通的不透明屏幕或透明屏幕

+ Add a normal Flutter screen

> *step 1: Add FlutterActivity to AndroidManifest.xml*
> 
> Flutter 提供 FlutterActivity 实现在 Android 应用程序中显示 Flutter 界面。与任何其他 Activity 一样，FlutterActivity 必须在 AndroidManifest.xml中注册。将以下 XML 添加到 AndroidManifest.xml 的 application tag 下：

```
<activity
  android:name="io.flutter.embedding.android.FlutterActivity"
  android:theme="@style/LaunchTheme"
  android:configChanges="orientation|keyboardHidden|keyboard|screenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
  android:hardwareAccelerated="true"
  android:windowSoftInputMode="adjustResize"
  />
```

> 对 @style/LaunchTheme 的引用可以被任何想要应用到 FlutterActivity 的 Android 主题所替代。主题的选择决定了应用于 Android 系统chrome的颜色，比如Android的导航栏，以及 Flutter UI 第一次呈现之前 FlutterActivity 的背景色
> 
> *Step 2: Launch FlutterActivity*
> 
> 在清单文件中注册了 FlutterActivity 后，可从应用程序中的任何位置启动 FlutterActivity。下面的示例显示了从 OnClickListener 启动的 FlutterActivity

```
// ExistingActivity.java

myButton.setOnClickListener(new OnClickListener() {
  @Override
  public void onClick(View v) {
    startActivity(
      FlutterActivity.createDefaultIntent(currentActivity)
    );
  }
});
```

> 前面的例子假设 Dart 入口点为main（），并且初始 Flutter 路径是'/'。无法使用Intent更改 Dart 入口点，但可以使用Intent更改初始路由。下面的示例演示如何启动 FlutterActivity，呈现自定义初始路由

```
// ExistingActivity.java

myButton.addOnClickListener(new OnClickListener() {
  @Override
  public void onClick(View v) {
    startActivity(
      FlutterActivity
        .withNewEngine()
        .initialRoute("/my_route")
        .build(currentActivity)
      );
  }
});
```

> 使用 withNewEngine（）工厂方法可以为当前 FlutterActivity 配置在内部创建的FlutterEngine 实例。这需要比较长的初始化时间。另一种方法是指示 FlutterActivity 使用预先创建并缓存的 FlutterEngine，这将使 Flutter 的初始化时间最小化
> 
> *Step 3: (Optional) Use a cached FlutterEngine*
> 
> 默认情况下，每个 FlutterActivity 都会创建自己的 FlutterEngine 。每个 FlutterEngine 都有比较长的创建时间。这意味着标准 FlutterActivity 的启动会有短暂的延迟。为了减少延迟，可以预先创建 FlutterEngine 
> 
> 要预先创建 FlutterEngine ，请在应用程序中找到一个合理的位置来实例化 FlutterEngine 。以下示例在 Application 类中预先创建 FlutterEngine ：

```
// MyApplication.java

public class MyApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();
    // Instantiate a FlutterEngine.
    flutterEngine = new FlutterEngine(this);

    // Start executing Dart code to pre-warm the FlutterEngine.
    flutterEngine.getDartExecutor().executeDartEntrypoint(
      DartEntrypoint.createDefault()
    );

    // Cache the FlutterEngine to be used by FlutterActivity.
    FlutterEngineCache
      .getInstance()
      .put("my_engine_id", flutterEngine);
  }
}
```

> 传递给 FlutterEngine 的ID可以是任意字串，但要确保将同一ID传递给将使用缓存的 FlutterEngine 的 FlutterActiity 或 FlutterFragment
> 
> 要预先创建 FlutterEngine ，必须执行 Dart 入口点。请记住，在调用executedEntryPoint（）时，Dart 入口点方法开始执行。如果Dart入口点调用 runApp(）来运行 Flutter 应用程序，那么 Flutter 应用程序的行为就像它在零尺寸的窗口中运行一样，直到此 FlutterEngine 连接到 FlutterActiity、FlutterFragment 或 FlutterView。确保你的应用程序在预先创建 FlutterEngine 和显示 Flutter 内容之间的行为正常
> 
> 有了预先创建且缓存的 FlutterEngine，现在需要指示 FlutterActivity 使用缓存的FlutterEngine，而不是创建新的FlutterEngine。要实现这一点，请使用 FlutterActivity 的withCachedEngine（）生成器：

```
// ExistingActivity.java

myButton.addOnClickListener(new OnClickListener() {
  @Override
  public void onClick(View v) {
    startActivity(
      FlutterActivity
        .withCachedEngine("my_engine_id")
        .build(currentActivity)
      );
  }
});
```

> 当使用缓存的 FlutterEngine 时，该 FlutterEngine 的生命周期比显示它的任何 FlutterActivity 或 FlutterFragment 都要长。请记住，只要预先创建 FlutterEngine ，Dart代码就开始执行，并在 FlutterActivity/FlutterFragment 销毁后继续执行。要停止执行并清除资源，可从 FlutterEngineCache 获取FlutterEngine 并使用 FlutterEngine.destroy（）销毁 FlutterEngine
> 
> 运行时性能并不是预先创建和缓存 FlutterEngine 的唯一原因。预先创建 FlutterEngine 执行 Dart 代码独立于 FlutterActivity，这使得 FlutterEngine 可以在任何时刻执行任意的 Dart 代码。非UI应用程序逻辑可以在 FlutterEngine（如网络和数据缓存）中执行，也可以在服务或其他地方的后台行为中执行。当使用 FlutterEngine 在后台执行时，要遵守Android对后台执行的所有限制
> 
> Flutter 的调试/发布版本具有截然不同的性能特征。要评估 Flutter 性能，使用发布版本
> 
> *Initial route with a cached engine*
> 
> 当使用新的 FlutterEngine 配置 FlutterActivity 或 FlutterFragment 时，初始路由的概念是可用的。然而，当使用缓存 FlutterEngine 时，FlutterActivity 和 FlutterFragment 不提供初始路由的概念。这是因为缓存的 FlutterEngine 已经在运行Dart代码，这意味着配置初始路由太迟了
> 
> 可以在执行 Dart 的入口点之前配置预先创建的 FlutterEngine 的初始路由：

```
// MyApplication.java

public class MyApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();
    // Instantiate a FlutterEngine.
    flutterEngine = new FlutterEngine(this);
    // Configure an initial route.
    flutterEngine.getNavigationChannel().setInitialRoute("your/route/here");
    // Start executing Dart code to pre-warm the FlutterEngine.
    flutterEngine.getDartExecutor().executeDartEntrypoint(
      DartEntrypoint.createDefault()
    );
    // Cache the FlutterEngine to be used by FlutterActivity or FlutterFragment.
    FlutterEngineCache
      .getInstance()
      .put("my_engine_id", flutterEngine);
  }
}
```

> 通过设置 navigation channel 的初始路由，关联的 FlutterEngine 在初始执行runApp（）Dart函数时显示所指定的界面

+ Add a translucent Flutter screen

> 一些应用程序希望部署一个看起来像模态的 Flutter 屏幕，例如对话框或 bottom sheet 。Flutter 支持半透明 FlutterActivity
> 
> *Step 1: Use a theme with translucency*
> 
> 对于使用半透明背景渲染的 Activity，Android需要一个特殊的主题属性。使用以下属性创建或更新Android主题：

```
<style name="MyTheme" parent="@style/MyParentTheme">
  <item name="android:windowIsTranslucent">true</item>
</style>
```

> 然后，将半透明的主题应用到 FlutterActivity 中

```
<activity
  android:name="io.flutter.embedding.android.FlutterActivity"
  android:theme="@style/MyTheme"
  android:configChanges="orientation|keyboardHidden|keyboard|screenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
  android:hardwareAccelerated="true"
  android:windowSoftInputMode="adjustResize"
  />
```

> *Step 2: Start FlutterActivity with transparency*
> 
> 要在透明背景下启动 FlutterActivity，请将适当的背景模式传递给IntentBuilder：

```
// ExistingActivity.java

// Using a new FlutterEngine.
startActivity(
  FlutterActivity
    .withNewEngine()
    .backgroundMode(FlutterActivity.BackgroundMode.transparent)
    .build(context)
);

// Using a cached FlutterEngine.
startActivity(
  FlutterActivity
    .withCachedEngine("my_engine_id")
    .backgroundMode(FlutterActivity.BackgroundMode.transparent)
    .build(context)
);
```

> 确保 Flutter 内容也包括一个半透明的背景。如果 Flutter UI 绘制了一个纯色的背景，那么它仍然看起来 FlutterActivity 有一个不透明的背景

#### [Adding a Flutter Fragment to an Android app](https://flutter.dev/docs/development/add-to-app/android/add-flutter-fragment)

### Adding to an IOS app

#### [Integrate a Flutter module into your iOS project](https://flutter.dev/docs/development/add-to-app/ios/project-setup)

+ 可以将 Flutter 作为嵌入式框架添加到现有的IOS应用程序中

+ System requirements

> 开发环境必须满足安装了 Xcode 的 Flutter 的 macOS 系统要求。Flutter 支持 iOS8.0 及更高版本

+ Create a Flutter module

> 要将 Flutter 嵌入到现有的应用程序中，首先创建一个 Flutter 模块

```
cd some/path/
flutter create --template module my_flutter
```

> Flutter 模块项目在 some/path/my_flutter/ 创建。从该目录中，可以运行与在任何其他flutter项目中相同的flutter命令，如 flutter run--debug 或 flutter build ios。还可以使用 Flutter 和 Dart 插件在 Android Studio/IntelliJ 或 VS Code 中运行该模块。此项目包含模块的单视图示例版本，然后嵌入到现有的应用程序中，这对于增量测试代码的 Flutter 部分非常有用

+ Module organization

> my_flutter 模块目录结构类似于常规 Flutter 应用：

```
my_flutter/
├── .ios/
│   ├── Runner.xcworkspace
│   └── Flutter/podhelper.rb
├── lib/
│   └── main.dart
├── test/
└── pubspec.yaml
```

> 在 lib/ 下添加代码；在 my_flutter/pubspec.yaml 里添加依赖
> 
> .ios/ 隐含子文件夹包含一个 Xcode workspace，可以在其中运行模块的独立版本。它是一个包装程序，用于引导 Flutter 代码，并包含帮助脚本，以帮助构建框架或将模块嵌入到现有应用程序中，与 CocoaPods 一起使用
> 
> 在已有应用或插件下添加 IOS 代码，不要在 .ios/ 下添加。针对 .ios/ 目录下的修改不会出现在调用该模块的原有应用中。Flutter 可能覆盖 .ios/
> 
> 因为 .ios/ 是自动生成的，不要对该目录进行源码管理

+ Embed the Flutter module in your existing application

> 在现有的应用程序中有两种嵌入 Flutter 的方法:
> 
> 使用 CocoaPods 依赖关系管理器并安装 Flutter SDK（推荐）
> 
> 为 Flutter engine 、编译的Dart代码和所有 Flutter 插件创建框架。手动嵌入框架，并在 Xcode 中更新现有应用程序的构建设置
> 
> 由于Flutter不支持输出 x86 的 AOT 二进制文件，因此该应用不能以发布模式在模拟器上运行。可以在模拟器或实际设备上以调试模式运行，以及在实际设备上以发布模式运行
> 
> *Option A - Embed with CocoaPods and the Flutter SDK*
> 
> 此方法要求在项目中工作的每个开发人员都有一个本地安装的 Flutter SDK 版本。只需在 Xcode 中构建应用程序，自动运行脚本来嵌入 Dart 和插件代码。这允许快速迭代最新版本的 Flutter 模块，而无需在 Xcode 之外运行其他命令
> 
> 下面的示例假定现有的应用程序和 Flutter 模块都在兄弟目录中。如果目录结构不同，则可能需要调整相对路径：

```
some/path/
├── my_flutter/
│   └── .ios/
│       └── Flutter/
│         └── podhelper.rb
└── MyApp/
    └── Podfile
```

> 如果现有的应用程序（MyAPP）还没有 Podfile，请遵循 [CocoaPods getting started guide](https://flutter.dev/docs/development/add-to-app/ios/project-setup)，将 CocoaPods 添加到项目中
> 
> *1.Add the following lines to your Podfile:*

```
// MyApp/Podfile

flutter_application_path = '../my_flutter'
load File.join(flutter_application_path, '.ios', 'Flutter', 'podhelper.rb')
```

> *2.对于每个需要嵌入 Flutter 的 Podfile target ，调用： `install_all_flutter_pods(flutter_application_path)`*

```
// MyApp/Podfile

target 'MyApp' do
  install_all_flutter_pods(flutter_application_path)
end
```

> *3.运行：pod install*
> 
> 当更改 my_flutter/pubspec.yaml 中的 Flutter 插件依赖项时，在 Flutter 模块目录中运行 flutter pub get 以刷新 podhelper.rb 脚本读取的插件列表。然后，从应用程序中的 some/path/MyApp 再次运行 pod install
> 
> podhelper.rb 脚本将插件、Flutter.framework 和 App.framework 嵌入到项目中
> 
> 应用的调试和发布构建配置分别嵌入了 Flutter 的调试和发布构建模式。
> 
> Flutter.framework 是 Flutter engine 包，App.framework 是为这个项目的编译的Dart代码
> 
> 在 Xcode 中打开 MyApp.xcworkspace，使用 `⌘B` 来构建工程
> 
> *Option B - Embed frameworks in Xcode*
> 
> 或者，可以通过手动编辑现有的 Xcode 项目来生成必要的框架并将它们嵌入到应用程序中。如果您的团队成员不能在本地安装 Flutter SDK 和 CocoaPods，或者如果您不想在现有应用程序中使用 CocoaPods 作为依赖管理器，那么您可以这样做。每次在 Flutter 模块中进行代码更改时，都必须运行 flutter build ios-framework
> 
> 下面的示例假设将框架生成到 some/path/MyApp/Flutter/

```
flutter build ios-framework --output=some/path/MyApp/Flutter/
```

```
some/path/MyApp/
└── Flutter/
    ├── Debug/
    │   ├── Flutter.framework
    │   ├── App.framework
    │   ├── FlutterPluginRegistrant.framework
    │   └── example_plugin.framework (each plugin with iOS platform code is a separate framework)
    ├── Profile/
    │   ├── Flutter.framework
    │   ├── App.framework
    │   ├── FlutterPluginRegistrant.framework
    │   └── example_plugin.framework
    └── Release/
        ├── Flutter.framework
        ├── App.framework
        ├── FlutterPluginRegistrant.framework
        └── example_plugin.framework
```

> 安装了Xcode 11之后，可以通过添加标志 ` --xcframework --no-universal` 来生成 XCFrameworks 而不是 universal frameworks
> 
> 在 Xcode 中将生成的 Flutter 框架嵌入或链接进已经存在的 IOS 工程中
> 
> 例如，可以将框架在Finder中从 some/path/MyApp/Flutter/Release/ 拖到目标的 build settings > Build Phases > Link Binary With Libraries 中
> 
> 在目标的  build settings 中，向  Framework Search Paths (FRAMEWORK_SEARCH_PATHS) 中添加 $(PROJECT_DIR)/Flutter/Release/ 

#### [Adding a Flutter screen to an iOS app](https://flutter.dev/docs/development/add-to-app/ios/add-flutter-screen)

+ 本指南介绍如何在现有的iOS应用程序中添加单个 Flutter 屏幕

+ Start a FlutterEngine and FlutterViewController

> 要从现有的iOS启动 Flutter 屏幕，可以启动 FlutterEngine 和 FlutterViewController
> 
> FlutterEngine 充当Dart虚拟机和 Flutter 运行时的宿主，FlutterViewController 连接到 FlutterEngine 以将 UIKit 输入事件传递到 Flutter 并显示由 FlutterEngine 渲染的帧
> 
> FlutterEngine 的寿命可能与 FlutterViewController 相同，或者比 FlutterViewController 的寿命长
> 
> 通常建议为应用预先创建一个长寿命的 FlutterEngine，因为：
> 
> 1.FlutterViewController 显示的更快
> 
> 2.Flutter 和 Dart 的状态比 FlutterViewController 寿命长
> 
> 3.在显示UI之前，IOS应用和插件可以和 Flutter 和 Dart 的逻辑进行交互
>
> *Create a FlutterEngine*
>
> 创建 FlutterEngine 的合适位置是特定于宿主应用程序的。作为一个例子，演示了在app delegate 的 app startup 时创建一个 FlutterEngine，并将其作为属性暴露出来
> 
> **AppDelegate.h:**

```
@import UIKit;
@import Flutter;

@interface AppDelegate : FlutterAppDelegate // More on the FlutterAppDelegate below.
@property (nonatomic,strong) FlutterEngine *flutterEngine;
@end
```

> **AppDelegate.m**

```
#import <FlutterPluginRegistrant/GeneratedPluginRegistrant.h> // Used to connect plugins.

#import "AppDelegate.h"

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary<UIApplicationLaunchOptionsKey, id> *)launchOptions {
  self.flutterEngine = [[FlutterEngine alloc] initWithName:@"my flutter engine"];
  // Runs the default Dart entrypoint with a default Flutter route.
  [self.flutterEngine run];
  [GeneratedPluginRegistrant registerWithRegistry:self.flutterEngine];
  return [super application:application didFinishLaunchingWithOptions:launchOptions];
}

@end
```

> *Show a FlutterViewController with your FlutterEngine*
>
> 下面的示例显示了一个通用的 ViewController，其中一个 UIButton 被钩住以显示 FlutterViewController。 FlutterViewController 使用在 AppDelegate 中创建的 FlutterEngine 实例
> 
> **ViewController.m**

```
@import Flutter;
#import "AppDelegate.h"
#import "ViewController.h"

@implementation ViewController
- (void)viewDidLoad {
    [super viewDidLoad];

    // Make a button to call the showFlutter function when pressed.
    UIButton *button = [UIButton buttonWithType:UIButtonTypeCustom];
    [button addTarget:self
               action:@selector(showFlutter)
     forControlEvents:UIControlEventTouchUpInside];
    [button setTitle:@"Show Flutter!" forState:UIControlStateNormal];
    button.backgroundColor = UIColor.blueColor;
    button.frame = CGRectMake(80.0, 210.0, 160.0, 40.0);
    [self.view addSubview:button];
}

- (void)showFlutter {
    FlutterEngine *flutterEngine =
        ((AppDelegate *)UIApplication.sharedApplication.delegate).flutterEngine;
    FlutterViewController *flutterViewController =
        [[FlutterViewController alloc] initWithEngine:flutterEngine nibName:nil bundle:nil];
    [self presentViewController:flutterViewController animated:YES completion:nil];
}
@end
```

> 使用前面的示例，当调用 AppDelegate 中创建的 FlutterEngine 上的run时，默认Dart库的默认 main（）入口将被运行

> *Alternatively - Create a FlutterViewController with an implicit FlutterEngine*
>
> 作为上述示例的替代，可以让 FlutterViewController 隐式地创建自己的 FlutterEngine，而无需提前创建 FlutterEngine
> 
> 通常不建议这样做，因为按需创建 FlutterEngine 可能会在 FlutterViewController 出现与第一帧呈现之间引入明显的延迟。然而，如果很少显示 Flutter 屏幕，当没有好的启发式方法来确定何时应该启动 Dart 虚拟机，以及 Flutter 不需要在 FlutterViewController 之间保持状态时，这可能非常有用
> 
> 为了让 FlutterViewController 不使用已有的 FlutterEngine，省略对 FlutterEngine 的构造，并在构造 FlutterViewController 时不引用 FlutterEngine
> 
> **ViewController.m**

```
// Existing code omitted.
- (void)showFlutter {
  FlutterViewController *flutterViewController =
      [[FlutterViewController alloc] initWithProject:nil nibName:nil bundle:nil];
  [self presentViewController:flutterViewController animated:YES completion:nil];
}
@end
```

+ Using the FlutterAppDelegate

> 建议使用应用程序的 UIApplicationDelegate 子类 FlutterAppDelegate，但不是必需的
> 
> FlutterAppDelegate 具有下述功能：
> 
> 将应用程序回调（如openURL）转发到插件（如local_auth）
> 
> 转发状态栏点击（只能在AppDelegate中检测到）以触发滚动到顶部的行为
> 
> 如果 app delegate 不能直接使 FlutterAppDelegate 成为一个子类，那么让 app delegate 实现 FlutterAppLifeCycleProvider 协议，以确保插件收到必要的回调。否则，依赖于这些事件的插件可能有未定义的行为
> 
> **AppDelegate.h**

```
@import Flutter;
@import UIKit;
@import FlutterPluginRegistrant;

@interface AppDelegate : UIResponder <UIApplicationDelegate, FlutterAppLifeCycleProvider>
@property (strong, nonatomic) UIWindow *window;
@property (nonatomic,strong) FlutterEngine *flutterEngine;
@end
```

> **AppDelegate.m**

```
@interface AppDelegate ()
@property (nonatomic, strong) FlutterPluginAppLifeCycleDelegate* lifeCycleDelegate;
@end

@implementation AppDelegate

- (instancetype)init {
    if (self = [super init]) {
        _lifeCycleDelegate = [[FlutterPluginAppLifeCycleDelegate alloc] init];
    }
    return self;
}

- (BOOL)application:(UIApplication*)application
didFinishLaunchingWithOptions:(NSDictionary<UIApplicationLaunchOptionsKey, id>*))launchOptions {
    self.flutterEngine = [[FlutterEngine alloc] initWithName:@"io.flutter" project:nil];
    [self.flutterEngine runWithEntrypoint:nil];
    [GeneratedPluginRegistrant registerWithRegistry:self.flutterEngine];
    return [_lifeCycleDelegate application:application didFinishLaunchingWithOptions:launchOptions];
}

// Returns the key window's rootViewController, if it's a FlutterViewController.
// Otherwise, returns nil.
- (FlutterViewController*)rootFlutterViewController {
    UIViewController* viewController = [UIApplication sharedApplication].keyWindow.rootViewController;
    if ([viewController isKindOfClass:[FlutterViewController class]]) {
        return (FlutterViewController*)viewController;
    }
    return nil;
}

- (void)touchesBegan:(NSSet*)touches withEvent:(UIEvent*)event {
    [super touchesBegan:touches withEvent:event];

    // Pass status bar taps to key window Flutter rootViewController.
    if (self.rootFlutterViewController != nil) {
        [self.rootFlutterViewController handleStatusBarTouches:event];
    }
}

- (void)application:(UIApplication*)application
didRegisterUserNotificationSettings:(UIUserNotificationSettings*)notificationSettings {
    [_lifeCycleDelegate application:application
didRegisterUserNotificationSettings:notificationSettings];
}

- (void)application:(UIApplication*)application
didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken {
    [_lifeCycleDelegate application:application
didRegisterForRemoteNotificationsWithDeviceToken:deviceToken];
}

- (void)application:(UIApplication*)application
didReceiveRemoteNotification:(NSDictionary*)userInfo
fetchCompletionHandler:(void (^)(UIBackgroundFetchResult result))completionHandler {
    [_lifeCycleDelegate application:application
       didReceiveRemoteNotification:userInfo
             fetchCompletionHandler:completionHandler];
}

- (BOOL)application:(UIApplication*)application
            openURL:(NSURL*)url
            options:(NSDictionary<UIApplicationOpenURLOptionsKey, id>*)options {
    return [_lifeCycleDelegate application:application openURL:url options:options];
}

- (BOOL)application:(UIApplication*)application handleOpenURL:(NSURL*)url {
    return [_lifeCycleDelegate application:application handleOpenURL:url];
}

- (BOOL)application:(UIApplication*)application
            openURL:(NSURL*)url
  sourceApplication:(NSString*)sourceApplication
         annotation:(id)annotation {
    return [_lifeCycleDelegate application:application
                                   openURL:url
                         sourceApplication:sourceApplication
                                annotation:annotation];
}

- (void)application:(UIApplication*)application
performActionForShortcutItem:(UIApplicationShortcutItem*)shortcutItem
  completionHandler:(void (^)(BOOL succeeded))completionHandler NS_AVAILABLE_IOS(9_0) {
    [_lifeCycleDelegate application:application
       performActionForShortcutItem:shortcutItem
                  completionHandler:completionHandler];
}

- (void)application:(UIApplication*)application
handleEventsForBackgroundURLSession:(nonnull NSString*)identifier
  completionHandler:(nonnull void (^)(void))completionHandler {
    [_lifeCycleDelegate application:application
handleEventsForBackgroundURLSession:identifier
                  completionHandler:completionHandler];
}

- (void)application:(UIApplication*)application
performFetchWithCompletionHandler:(void (^)(UIBackgroundFetchResult result))completionHandler {
    [_lifeCycleDelegate application:application performFetchWithCompletionHandler:completionHandler];
}

- (void)addApplicationLifeCycleDelegate:(NSObject<FlutterPlugin>*)delegate {
    [_lifeCycleDelegate addDelegate:delegate];
}
@end
```

+ Launch options

> 为了定制 Flutter 运行时，还可以指定 Dart 入口点、库和路由
> 
> *Dart entrypoint*
> 
> 调用 FlutterEngine 的 run，默认文件 lib/main.dart 中的 main() 函数
> 
> 可以使用 runWithEntrypoint 通过一个 NSString 指定一个不同的 Dart 入口函数
> 
> 除了main（）之外的 Dart 入口函数必须用以下方式进行注解，以便在编译时不会被 tree-shaken
> 
> **main.dart**

```
@pragma('vm:entry-point')
  void myOtherEntrypoint() { ... };
```

> *Dart library*
> 
> 除了指定Dart函数外，还可以在特定文件中指定入口点函数
> 
> 例如，以下命令在 lib/other_file.dart 中运行 myOtherEntrypoint（），而不是在 lib/main.dart 中运行main（）：

```
[flutterEngine runWithEntrypoint:@"myOtherEntrypoint" libraryURI:@"other_file.dart"];
```

> *Route*
> 
> 构建 FlutterEngine 时，可以为 Flutter WidgetsApp 设置初始路由：

```
FlutterEngine *flutterEngine =
    [[FlutterEngine alloc] initWithName:@"my flutter engine"];
[[flutterEngine navigationChannel] invokeMethod:@"setInitialRoute"
                                      arguments:@"/onboarding"];
[flutterEngine run];
```

### [Running, debugging, and hot reload](https://flutter.dev/docs/development/add-to-app/debugging)

+ 一旦将 Flutter 模块集成到项目中，并使用 Flutter 的平台api来运行 Flutter 引擎和/或UI，你就可以像运行普通的Android或iOS应用一样构建和运行你的Android或iOS应用

+ Flutter 通过 FlutterActivity 或 FlutterViewController 提升 UI 的能力

+ Debugging

> 除了在运行 flutter run 或在同等的 IDE 中获得各种 Flutter Debug 工具外，在 add-to-app 场景，也可以使用各种调试工具，比如：hot reload, performance overlays, DevTools, setting breakpoints。这些功能通过 flutter attach 机制提供
> 
> flutter attach 可以通过不同的途径启动，比如通过 SDK 的 CLI 工具，通过 VSCode 或 IntelliJ/Android Studio
> 
> 只要运行 FlutterEngine，flutter attach 可以连接，并保持连接，直到 FlutterEngine 被处置。但可以在启动 FlutterEngine 前启动 flutter attach 。flutter attach 等待由 FlutterEngine 托管的下一个可用的Dart虚拟机
> 
> 在 IntelliJ 或 VSCode 中，您应该选择 Flutter 模块运行的设备，以便 flutter attach 可以过滤正确的启动信号

+ Debugging specific instances of Flutter

> 可以向一个 app 上添加多个 Flutter 实例。flutter attach 默认会连接所有的 isolate。从相关的 CLI 发出的所有命令将被传递到所有被连接的 isolate
> 
> 通过从连接上的 Flutter CLI 工具中键入 l，可以列出所有连接的 isolate。如果未指定，则 isolate 名称根据 Dart 入口点文件名和函数名自动生成
> 
> 为了连接到特定的 isolate，请执行以下操作：
> 
> 1.在 Dart 源文件中对感兴趣的 Flutter root isolate 进行命名：

```
 // main.dart
 import 'dart:ui' as ui;

 void main() {
   ui.window.setIsolateDebugName("debug isolate");
   // ...
 }
```

> 2.使用 --isolate-filter 选项运行 flutter attach

```
 $ flutter attach --isolate-filter='debug'
 Waiting for a connection from Flutter...
 Done.
 Syncing files to device...      1.1s

 🔥  To hot reload changes while running, press "r".
 To hot restart (and rebuild state), press "R".
 An Observatory debugger and profiler is available
 at: http://127.0.0.1:43343/.
 For a more detailed help message,
 press "h". To detach, press "d"; to quit, press "q".

 Connected view:
   debug isolate (isolates/642101161)
```

### [Load sequence, performance, and memory](https://flutter.dev/docs/development/add-to-app/performance)

+ 本页描述了显示 Flutter UI 所涉及的步骤的分解。了解了这一点，可以更好地、明智地决定何时预热 FlutterEngine ，在哪个阶段哪些操作是可能的，以及这些操作的延迟和内存成本

+ Loading Flutter

> Android 和 iOS 应用程序（两个支持集成到现有应用程序的平台）、全 Flutter 应用程序和 add-to-app 模式在显示 Flutter UI时具有类似的概念加载步骤序列
> 
> *Finding the Flutter resources*
> 
> Flutter 的引擎运行时和应用程序编译的 Dart 代码都作为共享库捆绑在 Android 和 iOS 上。加载 Flutter 的第一步是在 .apk/.ipa/.app 中找到这些资源（以及其他 Flutter 资源，如图像、字体和JIT代码（如果适用））。当第一次在 Android 和  iOS APIs 上构建 FlutterEngine 时，就会发生这种情况
> 
> *Loading the Flutter library*
> 
> 找到后，FlutterEngine 的共享库在每个进程中加载一次内存
> 
> 在Android上，当JNI连接器需要引用 Flutter C++库时，也会发生这种情况。在iOS上，当 FlutterEngine 首次运行时会发生这种情况，例如运行 runWithEntrypoint:
> 
> *Starting the Dart VM*
> 
> Dart 运行时负责管理 Dart 内存和 Dart 代码的并发性。在 JIT 模式下，它还负责在运行时将 Dart 源代码编译为机器代码
> 
> 在 Android 和 iOS 上每个应用程序会话都存在一个 Dart 运行时
> 
> 在 Android 上首次构建 FlutterEngine 和在 iOS 上首次运行 Dart entrypoint 时，都会执行一次性的 Dart VM 启动
> 
> 此时，Dart代码的快照也会从应用程序的文件加载到内存中
> 
> Dart虚拟机启动后从不关闭
> 
> *Creating and running a Dart Isolate*
> 
> 在 Dart 运行时初始化之后，下一步是 Flutter engine 使用 Dart 运行时
> 
> 这是通过在Dart运行时启动 Dart Isolate 来完成的。Isolate 是 Dart 的内存和线程容器。在这个平台上还创建了一些辅助线程，以支持 Isolate，例如用于卸载GPU处理的线程和另一个用于图像解码的线程
> 
> 每个 Flutter engine 实例中存在一个 Isolate，多个 Isolate 可以由同一个 DART VM 托管
> 
> 在 Android 上，在 FlutterEngine 实例上调用 DartExecutor.executeDartEntrypoint() 时会发生这种情况
> 
> 在iOS上，当在 FlutterEngine 上调用 runWithEntrypoint: 时会发生这种情况
> 
> 此时，将执行 Dart 代码的选定入口点（默认情况下，是Dart库main.Dart文件的main（）函数）。如果在main（）函数中调用了 Flutter 函数runApp（），那么也会创建并构建 Flutter 应用程序或库的 widget 树。如果需要阻止在 Flutter 代码中执行某些功能，则 AppLifecycleState.distached 枚举值表示 FlutterEngine 未附加到任何 UI 组件，如 iOS 上的 FlutterViewController 或 Android 上的 FlutterActivity
> 
> *Attaching a UI to the Flutter engine*
> 
> 对于标准的全 Flutter 应用，应用一旦启动就会达到这个状态
> 
> 在 add-to-app 场景下，当将 FlutterEngine 连接到 UI 组件上会达到上述状态。具体方法可参见前几节。

+ Memory and latency

> 显示 Flutter 用户界面比较耗时。提前启动 FlutterEngine 可以降低这一成本
> 
> 对于 add-to-app 场景，最相关的选择是决定何时预加载 FlutterEngine（即加载Flutter库、启动Dart VM并在 isolate 中运行entrypoint），以及预加载的内存和延迟成本是多少。还需要知道当UI组件随后附加到 FlutterEngine 时，预加载如何影响渲染第一个 Flutter 帧的内存和延迟成本
> 
> 从 Flutter v1.10.3开始，在 release-AOT 模式下，对2015级低端设备进行测试，预加载 FlutterEngine 成本：
> 
> 42 MB和1530毫秒，可以在Android上预加载。其中330ms是主线程上的阻塞调用
> 
> 22 MB和860毫秒在iOS上预加载。260毫秒是对主线程的阻塞调用
> 
> 在预加载期间可以连接 Flutter 用户界面。剩余时间将加入到第一帧延迟时间
> 
> 在内存方面，一个成本样本（变量，取决于用例）可以是：
> 
> 创建pthread的大约4 MB操作系统内存使用量
> 
> 约10 MB GPU驱动程序内存
> 
> 约1 MB用于Dart运行时管理的内存
> 
> 大约5 MB用于加载Dart的字体映射
> 
> 就延迟而言，成本样本（根据用例的不同而变化）可以是：
> 
> 约20毫秒，从应用程序包中收集Flutter资产
> 
> 约15毫秒，打开 Flutter engine 库
> 
> 大约200毫秒以创建Dart虚拟机并加载AOT快照
> 
> 约200 ms，加载 Flutter 相关字体和资源
> 
> 大约400毫秒运行入口点，创建第一个窗口 widget 树，并编译所需的GPU着色器程序
> 
> Flutter engine 的预加载时间应足够晚，以延迟所需的内存消耗；但也应足够早，以避免 Flutter engine 的启动时间与显示 Flutter 的第一帧延迟相结合。确切的时间取决于应用程序的结构和启发式。例如，在通过 Flutter 绘制屏幕之前，将 Flutter engine 加载到屏幕中
> 
> 假设 Flutter engine 已预加载，用户界面附加的第一帧成本是：
> 
> 在Android上为320毫秒，额外的12 MB（高度依赖于屏幕的物理像素大小）
> 
> iOS上为200毫秒，额外16 MB（高度取决于屏幕的物理像素大小）
> 
> 内存方面，成本主要是用于渲染的图形内存缓冲区，并取决于屏幕大小
> 
> 就延迟而言，成本主要是等待操作系统回调为 Flutter 提供渲染图面，并编译无法预先预测的其余着色器程序。这是一次性费用
> 
> 当Flutter UI组件被释放时，UI相关的内存被释放。这不会影响 Flutter 状态，Flutter 状态存在于 Flutter engine 中（除非 Flutter engine 也被释放）

## Tools & techniques

### [Android Studio and IntelliJ](https://flutter.dev/docs/development/tools/android-studio)

### [Visual Studio Code](https://flutter.dev/docs/development/tools/vs-code)

### DevTools

#### [DevTools Overviews](https://flutter.dev/docs/development/tools/devtools/overview)

#### [Install and run DevTools from Android Studio](https://flutter.dev/docs/development/tools/devtools/android-studio)

#### [Install and run DevTools from VS Code](https://flutter.dev/docs/development/tools/devtools/vscode)

#### [Install and run DevTools from the command line](https://flutter.dev/docs/development/tools/devtools/cli)

#### [Using the Flutter inspector](https://flutter.dev/docs/development/tools/devtools/inspector)

#### [Using the Timeline view](https://flutter.dev/docs/development/tools/devtools/timeline)

#### [Using the Memory view](https://flutter.dev/docs/development/tools/devtools/memory)

#### [Using the Performance view](https://flutter.dev/docs/development/tools/devtools/performance)

#### [Using the debugger](https://flutter.dev/docs/development/tools/devtools/debugger)

#### [Using the Logging view](https://flutter.dev/docs/development/tools/devtools/logging)

### Flutter SDK

#### [Upgrading Flutter](https://flutter.dev/docs/development/tools/sdk/upgrading)

+ 无论你遵循哪一个 [Flutter release channels](https://github.com/flutter/flutter/wiki/Flutter-build-release-channels)，都可以使用 Flutter 命令来升级 Flutter SDK 和应用所依赖的软件包

> *Flutter's channels*
> 
> Flutter 具有以下通道，稳定性逐次递增：
> 
> **master**
> 
> The current tip-of-tree, absolute latest cutting edge build. Usually functional, though sometimes we accidentally break things
> 
> **dev**
> 
> 最新的全面测试版本。通常是功能性的，但是关于已知的“坏”dev构建的列表，请参见坏构建。我们不断地尝试将master滚动到dev，这样做需要运行比在master开发期间运行的更多的测试，这就是为什么这实际上与master不同
> 
> **beta**
> 
> 每个月，我们都会选择前一个月左右的“最佳”开发版本，并将其升级到beta版。这些构建已经过我们的代码实验室的测试
> 
> **stable**
> 
> 当我们相信我们有一个特别好的建设，我们促进它到稳定的渠道。我们打算每季度或多或少地这样做，但这可能有所不同。我们建议您将此频道用于所有生产应用程序版本。我们可能会为高优先级的错误将修补程序发送到稳定通道，尽管我们的目的是很少这样做

+ One-time setup

> 要使 Flutter 命令正常工作，应用程序的 pubspec.yaml 文件必须需要 Flutter SDK。例如，下面的代码片段指定 Flutter 和 flutter_test 需要 Flutter SDK：

```
name: hello_world
dependencies:
  flutter:
    sdk: flutter
dev_dependencies:
  flutter_test:
    sdk: flutter
```

> 不要使用 pub get 或 pub upgrade 命令来管理 Flutter 应用程序的依赖项。相反，使用 flutter pub get 或 flutter pub upgrade。如果要手动使用 pub，可以通过设置 FLUTTER_ROOT 环境变量直接运行它

+ Upgrading the Flutter SDK and packages

> 要同时更新 Flutter SDK 和应用程序所依赖的包，请使用应用程序根目录（包含 pubspec.yaml 文件的同一目录）中的 Flutter upgrade 命令：

```
$ flutter upgrade
```

> 这个命令首先获取 Flutter channel 上可用的 Flutter SDK 的最新版本。然后此命令将应用程序所依赖的每个包更新为最新的兼容版本
> 
> 如果您想要更新版本的 Flutter SDK，请切换到不太稳定的 Flutter channel，然后运行 `flutter upgrade`

+ Switching Flutter channels

> Flutter 有四个 release channel：stable、beta、dev和master。我们建议使用 stable 通道，除非您需要更新的版本
>
> 要查看当前 channel，请使用以下命令：

```
$ flutter channel
```

> 若要更改为另一个 channel，请使用 `flutter channel <channel-name>`。一旦你改变了你的 channel，使用 Flutter 升级下载 Flutter SDK 和依赖包。例如

```
$ flutter channel dev
$ flutter upgrade
```

+ Upgrading packages only

> 如果您修改了 pubspec.yaml 文件，或者只想更新应用程序所依赖的包（而不是包和 Flutter 本身），那么使用 flutter pub 命令之一
> 
> 要获取 pubspec.yaml 文件中列出的所有依赖项，而不进行不必要的更新，请使用 get 命令：

```
$ flutter pub get
```

> 要更新到 pubspec.yaml 文件中列出的所有依赖项的最新兼容版本，请使用 upgrade 命令：

```
$ flutter pub upgrade
```

+ Keeping informed

> 我们在 Flutter announcements 邮件列表中发布突破性的更改通知。您还可以在 Flutter dev 邮件列表上提问。除了订阅接收通知外，我们还希望收到您的来信

+ Selecting a specific version

> 如果要切换到特定版本的 Flutter，可以使用 Flutter version 命令：

```
$ flutter version v1.9.1+hotfix.3
```
> 要将包固定到特定版本，请在 pubspec.yaml 文件中显式指定其版本。有关此文件格式的详细信息，请参阅 dart.dev 上的 pubspec.yaml 文档

#### [Flutter SDK releases](https://flutter.dev/docs/development/tools/sdk/releases)

+ Stable channel (Windows、macOS、Linux) 列表
+ Beta channel (Windows、macOS、Linux) 列表
+ Dev channel (Windows、macOS、Linux) 列表
+ Master channel

> 安装包不可用于 master。但是，您可以通过克隆 master channel，然后触发 SDK 依赖项的下载，直接从GitHub repo获得SDK：

```
$ git clone -b master https://github.com/flutter/flutter.git
$ ./flutter/bin/flutter --version
```

#### [Breaking changes](https://flutter.dev/docs/release/breaking-changes)

+ no need to note

#### [Flutter release notes](https://flutter.dev/docs/development/tools/sdk/release-notes)

+ no need to note

### [Hot reload](https://flutter.dev/docs/development/tools/hot-reload)

+ Flutter 的热重新加载功能可以帮助您快速轻松地进行实验、构建 UI、添加功能和修复bug。热重新加载通过将更新的源代码文件注入正在运行的 Dart 虚拟机（VM）来工作。在 VM 用新版本的字段和函数更新类之后，Flutter 框架会自动重建小部件树，允许您快速查看更改的效果

+ 要热重新加载 Flutter 应用程序：

> 1.从支持的 Flutter 编辑器或终端窗口运行应用程序。目标可以是物理或虚拟设备。只有处于调试模式的 Flutter 应用程序才能热重新加载
> 
> 2.修改项目中的一个 Dart 文件。大多数类型的代码更改都可以热重新加载；有关需要热重新启动的更改列表，请参阅限制
> 
> 3.如果您在支持 Flutter IDE 工具的 IDE/编辑器中工作，请选择“全部保存”（cmd-s/ctrl-s），或单击工具栏上的“热重新加载”按钮；如果使用 flutter run 在命令行运行应用程序，请在终端窗口中输入 r
> 
> 在成功的热重新加载操作之后，您将在控制台中看到一条类似于：

```
Performing hot reload...
Reloaded 1 of 448 libraries in 978ms.
```

> 应用程序将更新以反映更改，并且应用程序的当前状态将保留上述示例中计数器变量的值。应用程序将继续从运行热重新加载命令之前的位置执行。代码更新并继续执行
> 
> 仅当修改后的 Dart 代码在更改后再次运行时，代码更改才具有可见效果。具体来说，热重新加载会导致所有现有的小部件重新生成。只有与小部件的重建相关的代码才会自动重新执行
> 
> 下一节将描述在热重新加载后修改的代码不会再次运行的常见情况。在某些情况下，对 Dart 代码的微小更改使您能够继续对应用程序使用热重新加载

+ Compilation errors

> 当代码更改导致编译错误时，热重新加载总是生成类似于以下内容的错误消息：

```
Hot reload was rejected:
'/Users/obiwan/Library/Developer/CoreSimulator/Devices/AC94F0FF-16F7-46C8-B4BF-218B73C547AC/data/Containers/Data/Application/4F72B076-42AD-44A4-A7CF-57D9F93E895E/tmp/ios_testWIDYdS/ios_test/lib/main.dart': warning: line 16 pos 38: unbalanced '{' opens here
  Widget build(BuildContext context) {
                                     ^
'/Users/obiwan/Library/Developer/CoreSimulator/Devices/AC94F0FF-16F7-46C8-B4BF-218B73C547AC/data/Containers/Data/Application/4F72B076-42AD-44A4-A7CF-57D9F93E895E/tmp/ios_testWIDYdS/ios_test/lib/main.dart': error: line 33 pos 5: unbalanced ')'
    );
    ^
```

> 在这种情况下，只需更正指定 Dart 代码行上的错误，以继续使用热重新加载

+ Previous state is combined with new code

> Flutter 的状态热重新加载保留了应用程序的状态。此设计使您能够仅查看最新更改的效果，而不丢弃当前状态。例如，如果你的应用需要用户登录，你可以在导航层次结构中修改和热重新加载几个级别的页面，而无需重新输入登录凭据。状态是保持的，这通常是期望的行为
> 
> 如果代码更改影响应用程序的状态（或其依赖项），则应用程序必须处理的数据可能与从头开始执行时的数据不完全一致。结果可能是热重新加载后的行为与热重新启动后的行为不同
> 
> 例如，如果将类定义从扩展 StatelessWidget 为 StatefulWidget（或相反），则在热重新加载之后，应用程序的前一个状态将保留。但是，状态可能与新更改不兼容
> 
> 考虑以下代码:

```
class MyWidget extends StatelessWidget {
  Widget build(BuildContext context) {
    return GestureDetector(onTap: () => print('T'));
  }
}
```

> 运行应用程序后，如果进行以下更改：

```
class MyWidget extends StatefulWidget {
  @override
  State<MyWidget> createState() => MyWidgetState();
}

class MyWidgetState extends State<MyWidget> { /*...*/ }
```

> 然后热重新加载；控制台显示一个断言失败，类似于：

```
MyWidget is not a subtype of StatelessWidget
```

> 在这些情况下，需要热重启才能看到更新的应用程序

+ Recent code change is included but app state is excluded

> 在 Dart 中，静态字段被延迟初始化。这意味着第一次运行 Flutter 应用程序并读取静态字段时，它将被设置为初始值设定项的值。全局变量和静态字段被视为状态，因此在热重新加载期间不会重新初始化
> 
> 如果更改全局变量和静态字段的初始值设定项，则需要完全重新启动才能查看更改。例如，请考虑以下代码:

```
final sampleTable = [
  Table("T1"),
  Table("T2"),
  Table("T3"),
  Table("T4"),
];
```

> 运行应用程序后，如果进行以下更改：

```
final sampleTable = [
  Table("T1"),
  Table("T2"),
  Table("T3"),
  Table("T10"),    // modified
];
```

> 然后热重新加载，更改不会反映出来
> 
> 相反，在以下示例中：

```
const foo = 1;
final bar = foo;
void onClick() {
  print(foo);
  print(bar);
}
```

> 首次运行应用程序将打印 1 和 1。然后，如果您进行以下更改：

```
const foo = 2;    // modified
final bar = foo;
void onClick() {
  print(foo);
  print(bar);
}
```

> 虽然对 const 字段值的更改总是热重新加载，但 static 字段初始值设定项不会重新运行。从概念上讲，const 字段被视为别名而不是 state
> 
> 当一组更改需要热重启才能生效时，Dart虚拟机会检测初始值设定项更改和标志。上述示例中的大多数初始化工作都会触发标记机制，但不适用于以下情况：

```
final bar = foo;
```

> 要在热重新加载后更新 foo 并查看更改，请考虑将该字段重新定义为 const 或使用 getter 返回值，而不是使用 final。例如：

```
const bar = foo;
```

> 或者

```
get bar => foo;
```

+ Recent UI change is excluded

> 即使热重新加载操作成功并且没有生成异常，某些代码更改也可能在刷新的UI中不可见。此行为在应用程序的main（）方法更改后很常见
> 
> 一般来说，如果修改后的代码位于根小部件的构建方法的下游，则热重新加载的行为与预期一致。但是，如果修改后的代码不会因为重新构建小部件树而重新执行，那么在热重新加载之后就看不到它的效果
> 
> 例如，请考虑以下代码：

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  Widget build(BuildContext context) {
    return GestureDetector(onTap: () => print('tapped'));
  }
}
```

> 运行此应用程序后，可以按如下方式更改代码：

```
import 'package:flutter/widgets.dart';

void main() {
  runApp(const Center(
      child: const Text('Hello', textDirection: TextDirection.ltr)));
}
```

> 通过热重启，程序从头开始，执行main（）的新版本，并构建显示文本Hello的小部件树
> 
> 但是，如果在此更改后重新热加载应用程序，则不会重新执行main（），并且将以未更改的MyApp实例作为根小部件重建小部件树。热重新加载后，结果没有明显变化

+ Limitations

> 您还可能遇到完全不支持热重新加载的罕见情况。其中包括：
> 
> initState（）上的更改不会由热重新加载反映。需要热重启
> 
> 枚举类型更改为常规类或常规类更改为枚举类型。例如，如果您更改:

```
enum Color {
  red,
  green,
  blue
}
```

> 为:

```
class Color {
  Color(this.i, this.j);
  final int i;
  final int j;
}
```

> 泛型类型声明被修改。例如，如果更改：

```
class A<T> {
  T i;
}
```

> 为:

```
class A<T, V> {
  T i;
  V v;
}
```

> 在这些情况下，热重新加载会生成诊断消息，并在不提交任何更改的情况下失败

+ How it works

> 调用热重新加载时，主机将查看自上次编译以来编辑的代码。将重新编译以下库：
> 
> 任何代码更改的库
> 
> 应用程序的主库
> 
> 从主库到受影响库的库
> 
> 在 Dart 2中，这些库的 Dart 源代码被转换为内核文件并发送到移动设备的 Dart 虚拟机
> 
> Dart 虚拟机从新内核文件重新加载所有库。到目前为止没有代码被重新执行
> 
> 热重新加载机制然后使 Flutter 框架触发对所有现有控件的重新构建/重新布局/重画和渲染对象

### [Code formatting](https://flutter.dev/docs/development/tools/formatting)

+ 尽管您的代码可能遵循我们经验丰富的开发团队中的任何首选样式，但他们可能会发现：

> 拥有单一的、共享的样式，并且
> 
> 通过自动格式化强制使用此样式
> 
> 另一种选择通常是在代码评审期间进行令人厌烦的格式化辩论，在代码评审期间，最好将时间花在代码行为上，而不是花在代码样式上

+ Automatically formatting code in Android Studio and IntelliJ

> 安装 Dart 插件以自动格式化 Android Studio 和 IntelliJ 中的代码
> 
> 若要在“当前源代码”窗口中自动格式化代码，请在“代码”窗口中单击鼠标右键，然后选择 `Reformat Code with dartfmt` 。您可以在 IntelliJ Preferences 的Keymap部分添加快捷键

+ Automatically formatting code in VS Code

> 安装 Flutter 扩展以获得 VS Code 中代码的自动格式化
> 
> 若要在当前源代码窗口中自动设置代码格式，请在代码窗口中单击鼠标右键，然后选择 Format Document。可以将键盘快捷键添加到此 VS Code Preferences

+ Automatically formatting code with the ‘flutter’ command

> 可以使用 flutter format 命令在命令行界面（CLI）中自动格式化代码：

```
$ flutter format path1 path2 ...
```

+ Using trailing commas

> Flutter 代码通常涉及构建相当深的树形数据结构，例如在 build 方法中。为了获得良好的自动格式，我们建议您采用可选的尾随逗号
> 
> 添加尾随逗号的原则很简单：在函数、方法和构造函数中的参数列表末尾添加尾随逗号，在这些位置您需要保留精心编制的格式
> 
> 这有助于自动格式化程序为 Flutter 样式的代码插入适当数量的换行符

## [AndroidX Migration](https://flutter.dev/docs/development/androidx-migration)

# Testing & debugging

## [Debugging Flutter apps](https://flutter.dev/docs/testing/debugging)

+ 有很多工具和特性可以帮助调试 Flutter 应用程序。以下是一些可用的工具：

> DevTools，一套在浏览器中运行的性能和分析工具
> 
> Android Studio/IntelliJ,VS code（启用 Flutter 和 Dart 插件）支持内置的源代码级调试器，能够设置断点、逐步执行代码和检查值
> 
> Flutter inspector 是 DevTools 中提供的一个小部件检查器，也可以直接从 Android Studio 和 IntelliJ（通过 Flutter 插件启用）。检查器允许检查小部件树的可视化表示、检查单个小部件及其属性值、启用性能覆盖等等

+ DevTools

> 对于调试和分析应用程序，DevTools 可能是您需要的第一个工具。DevTools 在浏览器中运行，支持多种功能：
> 源码级调试器
> 
> 显示可视化窗口小部件树的窗口小部件检查器，以及“widget select”模式，在该模式下，您可以在应用程序中选择窗口小部件，并深入到树中的该窗口小部件
> 
> 内存分析器
> 
> 支持跟踪、导入和导出跟踪信息的时间线视图
> 
> 日志视图
> 
> 如果在 debug 模式或 profile 模式下运行应用程序，则可以在浏览器中打开 DevTools 以连接到应用程序。DevTools 不能很好地处理编译为 release 模式的应用程序，因为调试和分析信息已经被剥离了
> 
> 如果使用 DevTools 进行分析，请确保在 profile 模式下运行应用程序。否则，出现在概要文件中的主要输出是验证框架的各种不变量的调试断言

+ Setting breakpoints

> 可以直接在 IDE/编辑器（比如 Android Studio/IntelliJ 和 VS code）中、在DevTools 调试器中或以编程方式设置断点

+ The Dart analyzer

> 如果使用的是支持 Flutter 的 IDE/编辑器，Dart 分析器已经在检查代码并寻找可能的错误
> 
> 如果从命令行运行，请使用 `flutter analyze` 测试代码
> 
> Dart 分析器大量使用您在代码中放置的类型注释来帮助跟踪问题。我们鼓励您在任何地方都使用它们（避免var、非类型化参数、非类型化列表文本等等），因为这是跟踪问题最快、最不痛苦的方法

+ Logging

> 另一个有用的调试工具是日志记录。以编程方式设置日志记录，然后在 DevTools 日志记录视图或控制台中查看输出

+ Debugging application layers

> Flutter 是用一个分层的架构设计的，它包括小部件、渲染和绘画层
> 
> Flutter窗口小部件检查器提供窗口小部件树的可视化表示，但是如果您想要更详细的级别，或者您想要窗口小部件树、层树或呈现树的基于文本的详细转储，请参见 [调试Flutter应用程序](https://flutter.dev/docs/testing/code-debugging#debug-flags-application-layers) 页面中的 [调试标志：应用程序层](https://flutter.dev/docs/testing/code-debugging)

+ Debug mode assertions

> 在开发过程中，强烈建议您使用 Flutter 的调试模式。如果在 Android Studio 中使用bug图标，或者在命令行运行flutter，则这是默认设置。一些工具通过命令行标志支持assert语句 --enable-asserts
> 
> 在这种模式下，Dart assert 语句被启用，Flutter 框架对执行期间遇到的每个 assert 语句的参数求值，如果结果为 false，则抛出异常。这允许开发人员启用或禁用不变量检查，以便相关的性能成本仅在调试会话期间支付
> 
> 当一个不变量被违反时，它会报告给控制台，并提供一些上下文信息来帮助跟踪问题的根源

+ Debugging animations

> 调试动画的最简单方法是减慢它们的速度。Flutter 检查器提供了一个慢速动画按钮，或者可以 [通过编程来降低动画的速度](https://flutter.dev/docs/testing/code-debugging#debugging-animations)
> 
> 有关调试 janky（非平滑）应用程序的更多信息，请参见 [Flutter 性能分析](https://flutter.dev/docs/perf/rendering/ui-performance)

+ Measuring app startup time

> 要收集有关 Flutter 应用程序启动所需时间的详细信息，可以使用 trace-startup 和 profile 选项运行 flutter run 命令

```
$ flutter run --trace-startup --profile
```

> 跟踪输出保存为名为 start_up_info.JSON 的 JSON 文件，位于 Flutter 项目的 build 目录下。输出列出从应用程序启动到这些跟踪事件（以微秒为单位捕获）所用的时间：
> 
> 进入 Flutter engine 代码的时间
> 
> 呈现应用程序第一帧的时间
> 
> Flutter 框架初始化时间
> 
> 完成 Flutter 框架初始化的时间
> 
> 例如：

```
{
  "engineEnterTimestampMicros": 96025565262,
  "timeToFirstFrameMicros": 2171978,
  "timeToFrameworkInitMicros": 514585,
  "timeAfterFrameworkInitMicros": 1657393
}
```

+ Tracing Dart code

> 要执行性能跟踪，可以使用DevTools时间线视图。时间线视图还支持导入和导出跟踪文件
> 
> 也可以通过编程方式执行跟踪，尽管这些跟踪不能导入DevTool的时间轴视图中
> 
> 在跟踪之前，请确保在 profile 模式下运行应用程序，以确保运行时性能特征与最终产品的性能特征非常匹配

+ Performance overlay

> 要获得应用程序性能的图形视图，打开 performance overlay。可以通过单击“Flutter 检查器”中的 `Performance Overlay` 按钮来执行此操作
> 
> 也可以通过编程方式打开 overlay

+ Common problems

> *“Too many open files” exception (MacOS)*
> 
> Mac OS一次可以打开多少文件的默认限制相当低。如果遇到此限制，请使用ulimit命令增加可用文件处理程序的数量：

```
ulimit -S -n 2048
```

> 如果使用 Travis 或 Cirrus 进行测试，请分别将同一行添加到 `flutter/.Travis.yml` 或 `flutter/.Cirrus.yml`，以增加它们可以打开的可用文件处理程序的数量

## [Debugging Flutter apps programmatically](https://flutter.dev/docs/testing/code-debugging)

+ 本文档描述了可以在代码中启用的调试功能

+ Logging

> 可以在 DevTools 的日志视图或系统控制台中查看日志
> 
> 有两个选择可用于输出日志。首先是使用 stdout 或 stderr。通常，这是使用 print（）语句完成的，或者通过导入 dart:io 并调用 stderr 和 stdout 上的方法来完成的。例如：

```
stderr.writeln('print me');
```

> 如果一次输出太多，那么 Android 有时会丢弃一些日志行。为了避免这一点，请使用foundation 库中的 debugPrint()。它对 print 进行了包装，将输出限制到一个避免被 Android 内核丢弃的级别
> 
> 另一个选择是使用 dart:developer log（）函数。这允许在日志输出中包含更多的粒度和信息。下面是一个例子：

```
import 'dart:developer' as developer;

void main() {
  developer.log('log me', name: 'my.app.category');

  developer.log('log me 1', name: 'my.other.category');
  developer.log('log me 2', name: 'my.other.category');
}
```

+ 还可以将应用程序数据传递给 `log()` 调用。使用 `error:` 命名参数调用 `log()` ，对要发送的对象进行 JSON 编码，并将编码的字符串传递给 `error` 参数

```
import 'dart:convert';
import 'dart:developer' as developer;

void main() {
  var myCustomObject = ...;

  developer.log(
    'log me',
    name: 'my.app.category',
    error: jsonEncode(myCustomObject),
  );
}
```

> 如果在 DevTool 的 logging 视图中查看日志输出， JSON 编码的错误参数将被解释为一个数据对象，并在该日志条目的 details 视图中呈现

+ Setting breakpoints

> 可以在 DevTools 的调试器或 IDE 的内置调试器中设置断点。如果要以编程方式设置断点，请使用以下说明:
> 
> 可以使用 debugger（）语句插入编程断点。要使用它，必须在相关文件的顶部导入 dart:developer 包
> 
> debugger（）语句接受一个可选的 when 参数，可以将其指定为仅在特定条件为 true 时中断，如下例所示：

```
import 'dart:developer';

void someFunction(double offset) {
  debugger(when: offset > 30.0);
  // ...
}
```

+ Debug flags: application layers

> Flutter 框架的每一层都提供一个函数，将当前状态或事件转储到控制台（使用debugPrint）
> 
> *Widget tree*
> 
> 要转储小部件库的状态，请调用 	`debugDumpApp（）`。只要应用程序至少构建了一次（换句话说，在调用 `runApp（）` 之后的任何时候），就可以在应用程序没有运行构建阶段的任何时候（换句话说，不在build（）方法中）或多或少地调用这个函数
> 
> 例如，以下应用程序：

```
import 'package:flutter/material.dart';

void main() {
  runApp(
    MaterialApp(
      home: AppHome(),
    ),
  );
}

class AppHome extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Material(
      child: Center(
        child: FlatButton(
          onPressed: () {
            debugDumpApp();
          },
          child: Text('Dump App'),
        ),
      ),
    );
  }
}
```

+ 前一个应用程序输出如下内容（具体细节因框架版本、设备大小等而异）：

```
I/flutter ( 6559): WidgetsFlutterBinding - CHECKED MODE
I/flutter ( 6559): RenderObjectToWidgetAdapter<RenderBox>([GlobalObjectKey RenderView(497039273)]; renderObject: RenderView)
I/flutter ( 6559): └MaterialApp(state: _MaterialAppState(1009803148))
I/flutter ( 6559):  └ScrollConfiguration()
I/flutter ( 6559):   └AnimatedTheme(duration: 200ms; state: _AnimatedThemeState(543295893; ticker inactive; ThemeDataTween(ThemeData(Brightness.light Color(0xff2196f3) etc...) → null)))
I/flutter ( 6559):    └Theme(ThemeData(Brightness.light Color(0xff2196f3) etc...))
I/flutter ( 6559):     └WidgetsApp([GlobalObjectKey _MaterialAppState(1009803148)]; state: _WidgetsAppState(552902158))
I/flutter ( 6559):      └CheckedModeBanner()
I/flutter ( 6559):       └Banner()
I/flutter ( 6559):        └CustomPaint(renderObject: RenderCustomPaint)
```

> 这是“展平”树，显示通过各种构建函数投影的所有小部件。（这是在小部件树的根上调用toStringDeep（）时获得的树。）您将看到许多小部件不出现在应用程序的源代码中，因为它们是由框架的小部件的构建函数插入的
> 
> 由于当按钮从按下变为释放时会调用 `debugDumpApp（）` 调用，因此它与调用 `setState（）` 的 FlatButton 对象一致，从而将自身标记为脏的。这就是为什么，当您查看转储时，应该看到标记为“dirty”的特定对象。您还可以看到注册了哪些手势监听器；在本例中，列出了一个 gesturedector，它只监听一个“tap”手势（“tap”是 `tapegesturedector的toStringShort` 函数的输出）
> 
> 如果您编写自己的小部件，则可以通过重写 debugFillProperties（） 来添加信息。将[DiagnosticsProperty][[]对象添加到方法的参数中，并调用超类方法。这个函数是toString方法用来填充小部件描述的

+ Render tree

> 如果您试图调试布局问题，那么 Widgets 层的树可能不够详细。在这种情况下，可以通过调用 `debugDumpRenderTree（）` 来转储呈现树。与 `debugDumpApp（）` 一样，除了在布局或绘制阶段之外，可以随时或多或少地调用它。一般来说，从帧回调或事件处理程序调用它是最好的解决方案
> 
> 要调用 `debugDumpRenderTree（）`，需要将 `import'package:flutter/rendering.dart'；` 添加到源文件中

```
I/flutter ( 6559): RenderView
I/flutter ( 6559):  │ debug mode enabled - android
I/flutter ( 6559):  │ window size: Size(1080.0, 1794.0) (in physical pixels)
I/flutter ( 6559):  │ device pixel ratio: 2.625 (physical pixels per logical pixel)
I/flutter ( 6559):  │ configuration: Size(411.4, 683.4) at 2.625x (in logical pixels)
I/flutter ( 6559):  │
I/flutter ( 6559):  └─child: RenderCustomPaint
I/flutter ( 6559):    │ creator: CustomPaint ← Banner ← CheckedModeBanner ←
I/flutter ( 6559):    │   WidgetsApp-[GlobalObjectKey _MaterialAppState(1009803148)] ←
I/flutter ( 6559):    │   Theme ← AnimatedTheme ← ScrollConfiguration ← MaterialApp ←
I/flutter ( 6559):    │   [root]
I/flutter ( 6559):    │ parentData: <none>
I/flutter ( 6559):    │ constraints: BoxConstraints(w=411.4, h=683.4)
I/flutter ( 6559):    │ size: Size(411.4, 683.4)
......

```

> 这是根 RenderObject 对象的 toStringDeep（）函数的输出
> 
> 调试布局问题时，要查看的关键字段是 size 和 constraint 字段。constraint 沿着树向下流动，size 又向上流动

+ Layer tree

> 如果试图调试合成问题，可以使用 debugDumpLayerTree（）

+ Semantics tree

+ **还有一些没有看完**

## [Using an OEM debugger](https://flutter.dev/docs/testing/oem-debuggers)

## [Flutter's build modes](https://flutter.dev/docs/testing/build-modes)

+ Flutter 工具在编译应用程序时支持三种模式，在测试时支持 headless 模式。根据您在开发周期中的位置选择编译模式。你在调试你的代码吗？你需要分析信息吗？准备好部署应用程序了吗？

> 在开发过程中使用 debug 模式，如果要使用热重新加载
> 
> 要分析性能时使用 profile 模式
> 
> 准备发布应用程序时使用 release 模式

+ Debug

> 在调试模式下，应用程序安装为在物理设备、模拟器上进行调试
> 
> *移动应用程序的调试模式意味着：*
> 
> 断言已启用
> 
> 服务扩展已启用
> 
> 编译是为了快速开发和运行周期而优化的（但不是为了执行速度、二进制大小或部署）
> 
> 已启用调试，支持源代码级调试的工具（如DevTools）可以连接到进程
> 
> *web应用的调试模式意味着：*
> 
> 构建版本没有缩小，也没有进行 tree shaking 处理
> 
> 应用程序是用 dartdevc 编译器编译的，以便调试
> 
> 默认情况下，`flutter run` 编译为调试模式。IDE 支持这种模式。例如， Android Studio 提供了一个 `Run>Debug…` 菜单选项，以及一个绿色的 bug 图标，在项目页面上覆盖了一个小三角形
> 
> *注意：*
> 
> 热重新加载仅在调试模式下工作
> 
> 模拟器仅在调试模式下执行
> 
> 在调试模式下，应用程序性能可能很差。在实际设备上以 profile 模式测量性能

+ Release

> 当你想要最大的优化和最小的大小时，使用 Release 模式来部署应用程序。对于移动设备，Release 模式（模拟器或仿真器不支持）意味着：
> 
> 断言被禁用
> 
> 调试信息被删除
> 
> 调试被禁用
> 
> 编译是为快速启动、快速执行和较小的包大小而优化的
> 
> 服务扩展被禁用
> 
> *web应用的 Release 模式意味着：*
> 
> 构建被缩小了，并进行了 tree shaking
> 
> 应用程序是用 dart2js 编译器编译的，以获得最佳性能
> 
> `flutter run--release` 命令编译为 release 模式。IDE支持这种模式。例如， Android Studio 提供了 `Run>Run…` 菜单选项，以及项目页面上的三角形绿色 Run 按钮图标
> 
> 可以使用 `flutter build <target>` 将特定目标的编译为 release 模式

+ Profile

> 在 profile 模式下，一些调试功能被保留以便能分析应用程序的性能。仿真器和模拟器上的 profile 模式被禁用，因为它们的行为不代表实际性能。在移动设备上，profile 模式与 release 模式类似，但有以下区别：
> 
> 某些服务扩展（例如启用 performance overlay ）已启用
> 
> 已启用跟踪，支持源代码级调试的工具（如 DevTools ）可以连接到进程
> 
> web应用的 profile 模式意味着：
> 
> 构建没有缩小，但 `tree shaking` 被执行
> 
> 应用程序是用 dart2js 编译器编译的
> 
> IDE 支持这种模式。例如，Android Studio 提供了 `Run>Profile…` 菜单选项。Flutter 运行命令 `flutter run --profile` 为 profile 模式
> 
> 使用 DevTools 套件分析应用程序的性能

## [Handling errors in Flutter](https://flutter.dev/docs/testing/errors)

+ Flutter 框架捕获由框架本身触发的回调期间发生的错误，包括在构建、布局和绘制期间

+ 所有这些错误都路由到 `FlutterError.onError` 处理程序。默认情况下，这将调用 `FlutterError.dumpErrorToConsole`，正如您可能猜到的，它将错误转储到设备日志。当从 IDE 运行时，检查器会重写此选项，以便错误也可以路由到 IDE 的控制台，从而允许您检查消息中提到的对象

+ 当在构建阶段发生错误时，将调用 `ErrorWidget.builder` 回调来构建使用的小部件，而不是失败的小部件。默认情况下，在 debug 模式下显示红色错误消息，在 release 模式下显示灰色背景

+ 通常，您可以通过将它们设置为 void main（）函数中的值来覆盖其中的每一个

+ 例如，要使应用程序在 release 模式中显示错误时立即退出，可以使用以下处理程序：

```
import 'dart:io';

import 'package:flutter/foundation.dart';
import 'package:flutter/material.dart';

void main() {
  FlutterError.onError = (FlutterErrorDetails details) {
    FlutterError.dumpErrorToConsole(details);
    if (kReleaseMode)
      exit(1);
  };
  runApp(MyApp());
}

// rest of `flutter create` code...
```

## [Testing Flutter apps](https://flutter.dev/docs/testing)

+ 应用程序的功能越多，手动测试就越困难。自动测试有助于确保应用程序在发布前正确运行，同时保留功能和错误修复速度

+ 自动测试分为几类：

> 单元测试测试单个函数、方法或类
> 
> 小部件测试（在其他UI框架中称为组件测试）测试单个小部件
> 
> 集成测试测试完整的应用程序或应用程序的大部分

+ 一般来说，一个经过良好测试的应用程序有许多单元和小部件测试，由代码覆盖率跟踪，加上足够的集成测试来覆盖所有重要的用例

+ Unit tests

> 单元测试测试单个函数、方法或类。单元测试的目标是在各种条件下验证逻辑单元的正确性。被测单元的外部依赖通常被模拟出来。单元测试通常不会从运行测试的进程外部读取或写入磁盘、呈现到屏幕或接收用户操作

+ Widget tests

> 小部件测试（在其他UI框架中称为组件测试）测试单个小部件。小部件测试的目标是验证小部件的UI看起来和交互是否如预期的那样。测试一个小部件涉及多个类，需要一个提供适当的小部件生命周期上下文的测试环境
> 
> 例如，被测试的小部件应该能够接收和响应用户操作和事件，执行布局，并实例化子小部件。因此，小部件测试比单元测试更全面。然而，与单元测试一样，小部件测试的环境被一个比成熟的UI系统简单得多的实现所取代

+ Integration tests

> 集成测试测试完整的应用程序或应用程序的大部分。集成测试的目标是验证正在测试的所有小部件和服务是否按预期协同工作。此外，您可以使用集成测试来验证应用程序的性能
> 
> 通常，集成测试在真实设备或操作系统仿真器（如 iOS 仿真器或 Android 仿真器）上运行。正在测试的应用程序通常与测试驱动程序代码隔离，以避免扭曲结果

+ Continuous integration services

> 持续集成（CI）服务允许您在推送新代码更改时自动运行测试。这提供了关于代码更改是否按预期工作的及时反馈，并且不会引入错误

# Performance & optimization

## [Measuring your app's size](https://flutter.dev/docs/perf/app-size)

+ 许多开发人员担心他们编译的应用程序的大小。由于 Flutter 应用程序的 APK、app bundle 或 IPA 版本是自包含的，并且包含运行该应用程序所需的所有代码和资产，因此其大小可能会引起关注。应用程序越大，它在设备上需要的空间就越多，下载时间也就越长，而且它可能会打破像 Android 即时应用（ Android instant app ）这样的有用功能的限制

+ 默认情况下，使用 flutter run 启动应用程序，或者单击 IDE 中的 Play 按钮（在试驾和编写第一个 Flutter 应用程序时使用），生成 Flutter 应用程序的调试版本。由于允许热重载和源代码级调试的开销，调试生成的应用程序大小很大

+ 生成最终用户版本 - Android

> 从 Flutter 项目的顶部运行以下命令，以获得32位Android设备的APK大小:

```
flutter build apk --target-platform=android-arm
```

> 输出应该如下所示：

```
Built build/app/outputs/apk/release/app-release.apk (4.2MB).
```

> 对于64位 Android 设备，运行以下命令：

```
flutter build apk --target-platform=android-arm64
```

> 下面是一个输出示例：

```
Built build/app/outputs/apk/release/app-release.apk (4.6MB).
```

> 运行以下命令来获取两个apk，一个用于32位，一个用于64位：

```
flutter build apk --split-per-abi
```

> 下面是一个输出示例：

```
Built build/app/outputs/apk/release/app-armeabi-v7a-release.apk (4.2MB).
Built build/app/outputs/apk/release/app-arm64-v8a-release.apk (4.6MB).
```

> 不要直接在 Flutter  1.9（或更高版本）中运行 flutter build apk，因为它会生成一个包含32位和64位二进制文件的胖 APK

+ 生成最终用户版本 - iOS

> 要大致了解发行版 IPA 的大小，运行以下命令：

```
flutter build ios && tar -zcf build/app.ipa build/ios/iphoneos/Runner.app && ls -lh build/app.ipa
```

> example/helloworld 应用程序生成的 IPA 文件为8.3 MB

```
-rw-r--r--  1 userName  primarygroup   8.3M Oct 25 13:47 build/app.ipa
```

> 按照 iOS create build archive 说明中的描述，通过创建发布归档文件可以获得更接近的结果。如果在项目中启用了 bitcode，则还可以选择从 bitcode 重建。如果此选项可用，则应选择此选项，以便更紧密地匹配应用商店将为您的应用程序生成的内容。您还可以为特定的手机架构选择应用程序精简，这应该非常接近该设备商店中的最终 IPA 大小
> 
> 要准确测量 iOS 应用程序，必须将发布版 IPA 上载到 Apple的app Store Connect（说明）并从中获取大小报告。IPAs 通常大于 APKs

+ Reducing app size

> 可以做一些显而易见的事情来缩小应用程序：
> 
> 删除未使用的资源
> 
> 最小化从库导入的资源
> 
> 支持有限数量的屏幕密度
> 
> 压缩PNG和JPEG文件

## Rendering performance

### [Improving rendering performance](https://flutter.dev/docs/perf/rendering)

+ 在应用程序中渲染动画是衡量性能时最引人关注的主题之一。部分归功于 Flutter 的 Skia 引擎以及它快速创建和处理 widget 的能力，Flutter 应用程序在默认情况下是有性能的，所以您只需要避免常见的陷阱就可以获得优异的性能

+ 如果您看到的是janky（非平滑）动画，请使用 profile 模式创建并分析应用程序的性能。默认的 Flutter 构建以调试模式创建一个应用程序，不用展现发布版本的性能

+ 几个常见的陷阱

> Rebuilding far more of the UI than expected each frame
> 
> Building a large list of children directly, rather than using a ListView

### [Performance best practices](https://flutter.dev/docs/perf/rendering/best-practices)

+ 一般来说，Flutter 应用程序在默认情况下是有性能的，因此只需要避免常见的陷阱就可以获得优异的性能，而不需要使用复杂的分析工具进行微观优化。这些最好的建议将帮助编写性能最好的 Flutter 应用程序

+ Best practices

> 如何设计一个 Flutter 应用程序，以最有效地渲染场景？特别是，如何确保框架生成的绘制代码尽可能高效？在设计应用程序时，需要考虑以下几点：
> 
> *Controlling build() cost*
> 
> 避免在build（）方法中重复和代价高昂的工作，因为在祖先 widget 重建时可以频繁调用build（）
> 
> 避免使用包含较大的 build() 函数的体量过大的 widget，根据封装和如何变化将其拆分成较小的 widget
> 当对 state 对象调用 setState（）时，所有子窗口 widget 都将重新生成。因此，将 setState（）调用局部化到其 UI 实际需要更改的子树部分。如果更改包含在树的一小部分，请避免在树的上部调用setState（）
> 
> 当重新遇到与前一帧相同的子小部件实例时，重建所有子部件的遍历将停止。此技术在优化动画的框架中被大量使用，其中动画不影响子树
> 
> *Apply effects only when needed*
> 
> 小心使用 effects（*动画效果*），因为它们可能很昂贵。其中一些在后台调用saveLayer（），这可能是一个昂贵的操作
> 
> 应用特定效果时的一些一般规则：
> 
> 仅在必要时使用不透明度 widget。有关将不透明度直接应用于图像的示例，请参见“不透明度API”页面中的“透明图像”部分，这比使用“不透明度” widget 更快
> 
> 剪裁（Clipping）不会调用saveLayer（）（除非使用Clip.antiAliasWithSaveLayer 显式请求），因此这些操作不像不透明操作那样昂贵，但剪裁仍然很昂贵，因此请谨慎使用。默认情况下，剪辑被禁用（ Clip.none ），因此必须在需要时显式启用它
> 
> 其他可能触发saveLayer（）并可能代价高昂的 widget：
> 
> ShaderMask
> 
> ColorFilter
> 
> Chip - 如果 `disabledColorAlpha != 0xff` 可能调用 `saveLayer()`
> 
> Text - 如果存在 `overflowShader`，可能会调用 `saveLayer（）`
> 
> 避免调用 `saveLayer（）` 的方法
> 
> 要在图像中实现淡入，请考虑使用 FadeInImage 小部件，该小部件使用 GPU 的片段着色器应用渐变不透明度。有关详细信息，请参见 [Opacity docs](https://api.flutter.dev/flutter/widgets/Opacity-class.html)
> 
> 要创建圆角矩形，而不是应用剪切矩形，请考虑使用许多小部件类提供的 borderRadius 属性
> 
> *Render grids and lists lazily*
> 
> 在构建大型网格或列表时，使用带有回调的 lazy 方法。这样，只有屏幕的可见部分在启动时生成
> 
> *Build and display frames in 16ms*
> 
> 由于有两个独立的线程用于生成和渲染，因此您有16ms用于生成，16ms用于在60Hz显示器上渲染。如果要考虑延迟，请在16毫秒或更短的时间内构建和显示帧。注意，这意味着在8ms或更短的时间内构建，在8ms或更短的时间内渲染，总共16ms或更短。如果缺少帧（jankyness）是一个问题，那么每个构建和渲染阶段的16ms是可以的
> 
> 如果您的帧在 profile 模式下的渲染速度远低于16ms，那么即使存在一些性能缺陷，您也不必担心性能问题，但是您仍然应该尽可能快地构建和渲染帧
> 
> 将帧渲染时间降低到16毫秒以下可能不会产生视觉差异，但它可以提高电池寿命和发热问题
> 
> 它可能在您的设备上运行良好，但请考虑针对目标设备的最低性能
> 
> 当120fps设备变得广泛可用时，为了提供最平滑的体验，您需要在8ms（总计）内渲染帧
> 
> 如果你想知道为什么60fps会带来流畅的视觉体验，请看视频为什么60fps？

+ Pitfalls

> 如果需要调整应用程序的性能，或者用户界面没有想象的那么平滑，IDE 的 Flutter 插件可以提供帮助。在 Flutter Performance 窗口中，启用“ `Show widget rebuild information` 复选框。此功能可帮助检测何时渲染和显示超过16毫秒的帧。在可能的情况下，插件提供指向相关提示的链接
> 
> 以下行为可能会对应用程序的性能产生负面影响:
> 
> 避免使用 Opacity widget，尤其是在动画中避免使用它。使用 AnimatedOpacity 或 FadeInImage 代替
> 
> 使用 AnimatedBuilder 时，请避免在 builder 函数中放置子树，该函数用于生成不依赖于动画的小部件。此子树是为动画的每个刻度重建的。相反，只需构建子树的那一部分，并将其作为子级传递给 AnimatedBuilder
> 
> 避免剪辑动画。如果可能，请在设置图像动画之前对其进行预剪辑
> 
> 如果大多数子项在屏幕上不可见，请避免将构造函数与子项的具体列表（如Column（）或ListView（））一起使用，以避免生成成本

### [Flutter performance profiling](https://flutter.dev/docs/perf/rendering/ui-performance)

+ Flutter 旨在提供每秒60帧（fps）的性能，或在能够120Hz更新的设备上提供每秒120帧的性能

+ 对于60FPS，帧需要渲染大约每16Ms

+ Jank 发生在 UI 渲染不顺利的时候。例如，每隔一段时间，一个帧需要10倍的时间来渲染，因此它会被丢弃，并且动画会明显地抖动

+ 有人说“一个快速的应用程序很好，但是一个平滑的应用程序更好。”如果你的应用程序渲染不平滑，你如何修复它？你从哪里开始？本指南将向您介绍从何处开始、要采取的步骤以及可以帮助您的工具

> 应用程序的性能由多个度量指标决定。性能有时指的是原始速度，但也指的是用户界面的平滑度和缺乏口吃( lack of stutter )。其他性能示例包括I/O或网络速度。本页主要关注第二类性能（UI平滑度），但您可以使用大多数相同的工具来诊断其他性能问题

+ 诊断性能问题

> 要诊断存在性能问题的应用程序，将启用性能覆盖来查看UI和GPU线程。在开始之前，需要确保是在 profile 模式下运行的，并且没有使用模拟器。为了获得最佳效果，可以选择用户可能使用的速度最慢的设备
> 
> *Connect to a physical device*
> 
> 几乎所有 Flutter 应用程序的性能调试都应该在物理Android或iOS设备上进行，且 Flutter 应用程序以 profile 模式运行。使用调试模式，或在模拟器上运行应用程序，通常并不表示发布模式生成的最终行为。应该考虑检查用户可能合理使用的最慢设备的性能
> 
> 为什么要在真正的设备上运行：
> 
> 模拟器和仿真器不使用相同的硬件，因此它们的性能特征不同：一些在模拟器上的操作比实际设备更快，一些则更慢
> 
> 调试模式需要启用一些额外的检查（比如断言等），这些操作在 profile 和 发布版本中不会执行，但却很昂贵
> 
> 调试模式也以不同于发布模式的方式执行代码。调试版本会在应用程序运行时编译 Dart 代码“即时”（JIT），但在应用程序加载到设备上之前，profile 和发布版本会预编译为本机指令（也称为“提前”或AOT）。JIT会导致应用程序暂停进行JIT编译，这本身会导致jank
> 
> *Run in profile mode*
> 
> Flutter 的 profile 模式编译和启动应用程序的方式与 release 模式几乎相同，但只有足够多的附加功能允许调试性能问题。例如，profile 模式为分析工具提供跟踪信息
> 
> 如下所示在 profile 模式下启动应用程序：
> 
> 在 Android Studio 或 IntelliJ 中，使用菜单项 `Run > Flutter Run main.dart in Profile Mode`
> 
> 在 VS Code 中，打开 launch.json 文件，并将 flutterMode 属性设置为profile 模式（完成 profiling 后，将其改回 release 或 debug 模式）：

```
"configurations": [
  {
    "name": "Flutter",
    "request": "launch",
    "type": "dart",
    "flutterMode": "profile"
  }
]
```

> 在命令行，使用 --profile 选项：

```
$ flutter run --profile
```

+ Launch DevTools

> DevTools 提供了一些特性，如分析、检查堆、显示代码覆盖率、启用性能覆盖率和逐步调试器。DevTools 的 Timeline 视图允许逐帧调查应用程序的UI性能
> 
> 当以 profile 模式运行时，启动 DevTools

+ The performance overlay

> 性能覆盖（performance overlay）以两个图表的形式显示统计信息，显示应用程序中的时间消耗情况。如果 UI 是janky（跳过帧），这些图将帮助找出原因。这些图表显示在运行的应用程序的顶部，但它们并不像一个普通的 widget 那样被绘制 —— Flutter engine 本身绘制了覆盖层（overlay），只对性能产生了最小的影响。每个图代表该线程的最后300帧
> 
> 本节介绍如何启用性能覆盖并使用它诊断应用程序中 jank 的原因。下面的屏幕截图显示了 Flutter Gallery 示例上运行的性能覆盖：
> 
> 显示GPU线程（顶部）和UI线程（底部）的性能覆盖图
> 
> 绿色竖条表示当前帧

+ 解释图表

> 上图显示了GPU线程的时间消耗，下图显示了UI（“CPU”）线程的时间消耗。沿着垂直轴的白色线条跨过图表显示16ms增量；如果图表越过其中一条线，则运行频率小于60Hz。水平轴表示帧。图表只是在应用绘制时更新，所以空闲则图表停止移动
> 
> 覆盖（overlay）应该始终在 profile 模式下查看，因为调试模式的性能是故意牺牲的，以换取旨在帮助开发的昂贵断言，因此结果是误导性的
> 
> 每个帧应该在 1/60秒（大约16ms）内被创建和显示。超过此限制的帧（在任一图形中）无法显示，导致jank，并且一个或两个图形中都会出现一个垂直的红色条。如果UI图中出现红色条，则 Dart 代码太耗时；如果GPU图中出现红色竖条，则场景太复杂，无法快速渲染

+ Flutter’s threads

> Flutter 使用几个线程来完成它的工作，尽管覆盖图(overlay)中只显示了其中的两个线程。所有的 Dart 代码都在 UI 线程上运行。尽管不能直接访问任何其他线程，但在UI线程上的操作会对其他线程产生性能影响
> 
> *Platform thread*
> 
> 平台的主线。插件代码在这里运行。有关更多信息，请参阅iOS的UIKit文档或Android的主线程文档。此线程未显示在性能覆盖中
> 
> *UI thread*
> 
> UI线程在 Dart 虚拟机中执行 Dart 代码。这个线程包括您编写的代码，以及 Flutter 框架代表应用程序执行的代码。当应用程序创建并显示场景时，UI 线程创建一个层树（layer tree），这是一个轻量级对象，包含与设备无关的绘制命令，并将层树发送到要在设备上呈现的GPU线程。不要阻塞这个线程！UI线程显示在性能覆盖图的最下面一行
> 
> *GPU thread*
> 
> GPU 线程获取层树，并通过与 GPU（图形处理单元）对话来显示它。不能直接访问 GPU 线程或它的数据，但是，如果这个线程很慢，这是在 Dart 代码中所做的一些事情的结果。Skia，图形库，运行在这个线程上，有时被称为光栅化线程。GPU 线程显示在性能覆盖图的第一行
> 
> *I/O thread*
> 
> 执行昂贵的任务（主要是I/O），否则会阻塞UI或GPU线程。此线程未显示在性能覆盖中

+ Displaying the performance overlay

> *Using the Flutter inspector*
> 
> 启用 Performance Overlay 小部件的最简单方法是使用 Flutter 检查器，它可以在 DevTools 的检查器视图中使用。只需单击 Performance Overlay（性能覆盖）按钮，即可在运行的应用程序上切换覆盖
> 
> *From the command line*
> 
> 使用命令行中的P键切换性能覆盖
> 
> *Programmatically*
> 
> 要以编程方式启用覆盖，请参阅[以编程方式调试颤振应用程序](https://flutter.dev/docs/testing/code-debugging)页面中的“性能覆盖”部分
> 
> 你可能对 Flutter Gallery 示例应用程序很熟悉。要使用 Flutter Gallery 的性能覆盖，请使用 Flutter 安装的 examples 目录中的副本，并在 profile 模式下运行应用程序。程序的编写使得应用程序菜单允许您动态切换覆盖，以及启用对 saveLayer 调用和缓存图像存在性的检查
> 
> 无法在从应用程序商店下载的 Flutter Gallery 应用程序中启用性能覆盖。该版本的应用程序被编译为发布模式（不是 profile 模式），并且不提供启用或禁用覆盖的菜单

+ Identifying problems in the UI graph

> 如果性能覆盖在UI图中显示为红色，则从分析Dart VM开始，即使GPU图也显示为红色

+ Identifying problems in the GPU graph

> 有时场景会生成一个易于构造但在 GPU 线程上渲染代价高昂的层树。当这种情况发生时，UI图没有红色，但是 GPU 图显示红色。在这种情况下，需要弄清楚代码正在做什么，这会导致呈现代码变慢。特定类型的工作负载对于GPU来说更为困难。它们可能涉及到对saveLayer的不必要调用、与多个对象相交的不透明性以及特定情况下的剪辑或阴影
> 
> 如果怀疑慢度的来源是在动画过程中，请单击 `Flutter inspector` 中的 `Slow Animations` 按钮，将动画慢5倍。如果希望对速度进行更多控制，也可以通过编程方式执行此操作
> 
> 是第一帧慢，还是整个动画慢？如果是整个动画，剪辑会导致速度减慢吗？也许有另一种不使用剪辑的方法来绘制场景。例如，将不透明的角点覆盖到正方形上，而不是剪切到圆角矩形上。如果是正在淡入、旋转或以其他方式操纵的静态场景，则重绘边界可能会有所帮助
> 
> *Checking for offscreen layers*
> 
> saveLayer 方法是 Flutter 框架中最昂贵的方法之一。当对场景应用后期处理时，它很有用，但它会减慢应用程序的速度，如果不需要，应该避免使用它。即使不显式调用saveLayer，隐式调用也可能发生。可以使用 PerformanceOverlayLayer.checkboard offscreenlayers 开关检查当前场景是否正在使用 saveLayer
> 
> 启用开关后，运行应用程序并查找任何用闪烁框勾勒的图像。如果正在渲染新帧，则框会在帧之间闪烁。例如，可能有一组对象具有使用saveLayer渲染的不透明性。在这种情况下，对每个单独的小部件应用不透明度可能比在小部件树的上方应用父小部件更有效。其他可能代价高昂的操作也一样，如剪辑或阴影
> 
> 不透明度、剪辑和阴影本身并不是一个坏主意。但是，将它们应用到小部件树的顶部可能会导致对saveLayer的额外调用，以及不必要的处理
> 
> 当遇到对saveLayer的调用时，请问自己以下问题：
> 
> 应用程序需要这种效果吗？
> 
> 这些调用能被取消吗？
> 
> 可以对单个元素而不是组应用相同的效果吗？
> 
> *Checking for non-cached images*
> 
> 在有意义的情况下，使用 RepaintBoundary 缓存图像是很好的
> 
> 从资源的角度来看，最昂贵的操作之一是使用图像文件渲染纹理。首先，压缩图像是从持久存储中提取的。图像被解压缩到主机内存（GPU内存），并传输到设备内存（RAM）
> 
> 换句话说，图像I/O可能很昂贵。缓存提供复杂层次结构的快照，以便在后续帧中更容易渲染。由于光栅缓存项在构建和占用GPU内存时非常昂贵，因此仅在绝对必要时才缓存图像
> 
> 通过启用 PerformanceOverlayLayer.checkboardRasterCacheImages 开关，可以看到正在缓存哪些图像
> 
> 运行应用程序并查找使用随机彩色棋盘显示的图像，指示图像已缓存。当您与场景交互时，棋盘图像应该保持不变，您不希望看到闪烁，这将表明缓存的图像正在被重新缓存
> 
> 在大多数情况下，您希望看到静态图像上的棋盘格，但不希望看到非静态图像上的棋盘格。如果没有缓存静态图像，可以将其放入RepaintBoundary小部件中进行缓存。如果引擎认为图像不够复杂，它可能仍然会忽略重新绘制的边界
> 
> *Viewing the widget rebuild profiler*
> 
> Flutter 框架的设计使其很难创建不是60fps和平滑的应用程序。通常，如果有jank，那是因为有一个简单的 bug 导致每帧要重建的 UI 比所需的要多。Widget rebuild profiler帮助调试和修复由于这些错误而导致的性能问题

+ Benchmarking

> 可以通过编写基准测试来衡量和跟踪应用程序的性能。Flutter 驱动程序库为基准测试提供支持。使用此集成测试框架，可以生成跟踪以下内容的度量：
> 
> Jank
> 
> 下载大小
> 
> 电池效率
> 
> 启动时间
> 
> 跟踪这些基准可以让您在引入对性能有不利影响的回归时得到通知

# Deployment

## [Creating flavors for Flutter](https://flutter.dev/docs/deployment/flavors)

## [Build and release an Android app](https://flutter.dev/docs/deployment/android)

+ 在典型的开发周期中，可以在命令行使用 flutter run 测试应用程序，或者使用 IDE 中的 Run 和 Debug 选项测试应用程序。默认情况下，Flutter 会生成应用程序的调试版本

+ 当您准备应用程序的发布版本（例如发布到Google Play商店）时，此页面可以提供帮助。在发布之前，您可能需要对应用程序进行一些最后的润色

+ Adding a launcher icon

> 当一个新的 Flutter 应用程序被创建时，它有一个默认的启动图标。要自定义此图标，可能需要查看 flutter_launcher_icons 包
> 
> 或者，可以使用以下步骤手动执行此操作：
> 
> 1.回顾 [材料设计产品图标设计指南](https://material.io/design/iconography/)
> 
> 2.在 <app dir>/android/app/src/main/res/ 目录中，将图标文件放在使用配置限定符命名的文件夹中。默认的 mipmap-folders 演示了正确的命名约定
> 
> 3.在 AndroidManifest.xml 中，将应用程序标记 android:icon 属性更新为引用上一步中的图标（例如，<application android:icon=“@mipmap/ic_launcher”…）
> 
> 4.要验证图标是否已被替换，请运行应用程序并检查启动程序中的应用程序图标

+ Signing the app

> 要在Play Store上发布，需要为应用程序提供数字签名。使用以下说明为应用程序签名
> 
> *Create a keystore*
> 
> 如果已有 keystore，跳过下一步。如果不是，请在命令行运行以下命令创建一个：
> 
> 在Mac/Linux上，使用以下命令：

```
keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
```

> 在Windows上，使用以下命令：

```
keytool -genkey -v -keystore c:/Users/USER_NAME/key.jks -storetype JKS -keyalg RSA -keysize 2048 -validity 10000 -alias key
```

> 保持 keystore 文件私有；不要将其签入公共源代码管理
> 
> keytool 命令可能不在您的路径中，它是作为Android Studio一部分安装的Java的一部分。对于具体路径，运行 flutter doctor -v 并定位在“Java binary at:”之后打印的路径。然后使用这个完全限定的路径，用 keytool 替换 java（在最后）。如果路径包含空格分隔的名称（如程序文件），请在空格分隔的名称周围加引号。例如：/"Program Files"/
> 
> -storetype JKS 标记仅对 Java9 或更新版本是必需的。从 Java 9 版本开始，keystore 类型默认为 PKS12

+ Reference the keystore from the app

> 创建一个名为 <app dir>/android/key.properties 的文件，其中包含对 keystore 的引用：

```
storePassword=<password from previous step>
keyPassword=<password from previous step>
keyAlias=key
storeFile=<location of the key store file, such as /Users/<user name>/key.jks>
```

+ Configure signing in gradle

> 通过编辑 <app dir>/android/app/build.gradle 文件为应用配置签名
> 
> 1.替换下述：

```
  android {
```

> 为下述内容：

```
   def keystoreProperties = new Properties()
   def keystorePropertiesFile = rootProject.file('key.properties')
   if (keystorePropertiesFile.exists()) {
       keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
   }

   android {
```

> 2.替换下述：

```
   buildTypes {
       release {
           // TODO: Add your own signing config for the release build.
           // Signing with the debug keys for now,
           // so `flutter run --release` works.
           signingConfig signingConfigs.debug
       }
   }
```

> 为下述内容：

```
   signingConfigs {
       release {
           keyAlias keystoreProperties['keyAlias']
           keyPassword keystoreProperties['keyPassword']
           storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
           storePassword keystoreProperties['storePassword']
       }
   }
   buildTypes {
       release {
           signingConfig signingConfigs.release
       }
   }
```

> 应用的发布版本现在将自动签名
> 
> 更改 gradle 文件后，可能需要运行 flutter clean。这将防止缓存的构建影响签名过程

+ R8

> R8 是来自 Google 的新代码收缩器，在构建一个发布版 APK 或 AAB 时默认启用它。若要禁用 R8，请传递 --no-shrink 标志来 flutter build apk 或 flutter build appbundle
> 
> 混淆和缩小可以大大延长Android应用程序的编译时间

+ Reviewing the app manifest

> 检查位于 <App dir>/android/App/src/main 中的默认应用程序清单文件 android Manifest.xml，并验证这些值是否正确，尤其是以下值：
> 
> *application*
> 
> 编辑 application 标签中的 android:label 以定义应用程序的最终名称
> 
> *uses-permission*
> 
> 如果应用程序代码需要访问 Internet，请添加 android.permission.INTERNET 权限。标准模板不包含此标记，但允许在开发期间访问 Internet，以便在 Flutter 工具和正在运行的应用程序之间进行通信

+ Reviewing the build configuration

> 查看位于 <app dir>/android/app 中的默认 Gradle 构建文件 build.Gradle，并验证这些值是否正确，尤其是 defaultConfig 块中的以下值：
> 
> *applicationId*
> 
> 指定最终的、唯一的（应用程序Id）appid
> 
> *versionCode & versionName*
> 
> 指定内部应用程序版本号和版本号显示字符串。可以通过在pubspec.yaml文件中设置version属性来完成此操作
> 
> *minSdkVersion & targetSdkVersion*
> 
> 指定应用程序运行的最低API级别和API级别

+ Building the app for release

> 发布到Play Store时有两种可能的发布格式:
> 
> App bundle（首选)
> 
> APK
> 
> *Build an app bundle*
> 
> 本节介绍如何构建发布应用程序包。如果您完成了签名步骤，应用程序包将被签名
> 
> 最近，Flutter 团队收到了几份来自开发者的报告，显示他们在 Android 6.0 上构建应用程序包时遇到了某些设备上的应用程序崩溃。当 Android 团队正在寻找一个可行的解决方案时，可以尝试将APK拆分，作为一个临时的解决方案
> 
> 从命令行：
> 
> 1.输入 `cd <app dir>`
> 
> 2.运行 `flutter build appbundle`
> 
> 应用程序的发行包创建于 `<app dir>/build/app/outputs/bundle/release/app.aab`
> 
> 默认情况下，app bundle 包含 Dart 代码和为 armeabi-v7a（ARM 32位）、arm64-v8a（arm64位）和x86-64（x86 64位）编译的 Flutter 运行时

+ Test the app bundle

> 应用程序包(app bundle)可以通过多种方式进行测试本节将介绍两种:
> 
> *Offline using the bundle tool*
> 
> 1.如果您还没有这样做，请从 [GitHub 存储库](https://github.com/google/bundletool/releases/tag/0.12.0) 下载 bundletool
> 
> 2.从应用程序包(app bundle)生成一组 APKs
> 
> 3.将 APK 部署到连接的设备
> 
> *Online using Google Play*
> 
> 1.把包上传到 Google Play 进行测试。您可以使用内部测试跟踪或 alpha 或 beta 通道来测试包，然后再将其发布到生产环境中
> 
> 2.按照 [这些步骤](https://developer.android.com/studio/publish/upload-bundle) 将包上载到Play Store

+ Build an APK

> 虽然 app bundle 比 APK 更受欢迎，但有些商店还不支持 app bundle。在这种情况下，为每个目标ABI（应用程序二进制接口）构建一个发布版 APK
> 
> 如果您完成了签名步骤，APK将被签名
> 
> 从命令行：
> 
> 1.输入 `cd <app dir>`
> 
> 2.运行 `flutter build apk --split-per-abi`
> 
> 此命令生成两个APK文件:
> 
> <app dir>/build/app/outputs/apk/release/app-armeabi-v7a-release.apk
> 
> <app dir>/build/app/outputs/apk/release/app-arm64-v8a-release.apk
> 
> <app dir>/build/app/outputs/apk/release/app-x86_64-release.apk
> 
> 删除 --split-per-abi 标志将生成一个fat APK，其中包含为所有目标 ABIs 编译的代码。这类 APK 的大小比其拆分的 APK 要大，这导致用户下载不适用于其设备架构的二进制文件

+ Install an APK on a device

> 按照以下步骤在连接的Android设备上安装APK:
> 
> 从命令行：
> 
> 1.使用USB电缆将Android设备连接到计算机
> 
> 2.输入 `cd <app dir>`
> 
> 3.运行 `flutter install`

+ Updating the app’s version number

> 应用程序的默认版本号为1.0.0。要更新它，请导航到pubspec.yaml文件并更新以下行：

```
version: 1.0.0+1
```

> 版本号是三个由点分隔的数字，如上面示例中的1.0.0，后面是可选的内部版本号，如上面示例中的1，由+分隔
> 
> 通过分别指定 --build-name 和 --build-number，Flutter 应用的版本号和内部版本号都可以在被覆盖
> 
> 在 Android 中，build-name 用作 versionName，build-number 用作versionCode

+ Android release FAQ

> *应该什么时候构建应用程序包(app bundles)和 APKs ？*
> 
> Google Play商店建议您使用 app bundles 而不是 APKs，因为它们允许更有效地将应用程序交付给用户。但是，如果您是通过 Google Play商店以外的方式分发应用程序，那么 APK 可能是您唯一的选择
> 
> *什么是 fat APK?*
> 
> fat APK 是单个 APK，它包含嵌入在其中的多个abi的二进制文件。这样做的好处是，单个APK运行在多个体系结构上，因此具有更广泛的兼容性，但它的缺点是其文件大小要大得多，导致用户在安装应用程序时下载和存储更多字节。当构建 APK 而不是 app bundle 时，强烈建议构建split APK（在创建 APK 时使用 --split-per-abi 选项）
> 
> *支持的目标体系结构是什么？*
> 
> 在发布模式下构建应用程序时，可以为armeabi-v7a（ARM 32位）、arm64-v8a（arm64位）和x86-64（x86 64位）编译Flutter应用程序。Flutter 目前不支持为 x86 Android构建
> 
> *如何在 Android Studio 中构建一个发布版本？*
> 
> 在 Android Studio 中，打开应用程序文件夹下的现有 android/ 文件夹。然后，在项目面板中选择 build.gradle（Module: app）：
> 
> 接下来，选择构建变量。单击主菜单中的 `Build > Select Build Variant`。在 `Build Variants` 面板中选择任何变量（默认为“调试”）
> 
> 生成的应用程序包(app bundle)或 APK 文件位于应用程序文件夹中的 `build/app/outputs` 中

## [Build and release an iOS app](https://flutter.dev/docs/deployment/ios)

+ 本指南提供了将 Flutter 应用程序发布到  App Store 和 TestFlight 的步骤

+ 有关混淆 Dart 代码的信息，请参见 [Obfuscating Dart Code](https://github.com/flutter/flutter/wiki/Obfuscating-Dart-Code)

+ 预备工作

> 在开始发布应用程序之前，请确保它符合 [苹果的应用程序审查指南](https://developer.apple.com/app-store/review/)
> 
> 要将应用程序发布到 App Store，您需要注册 [Apple Developer Program](https://developer.apple.com/programs/)
> 
> 您可以在Apple的 [ Choosing a Membership](https://developer.apple.com/support/compare-memberships/) 指南中阅读更多有关各种会员资格选项的信息

+ Register your app on App Store Connect

> App Store Connect（以前叫iTunes Connect）是管理应用程序生命周期的地方。您将定义应用程序名称和描述，添加屏幕截图，设置定价，并管理发布到 App Store 和 TestFlight 的版本
> 
> 注册应用程序包括两个步骤：注册唯一的Bundle ID和在app Store Connect上创建应用程序记录
> 
> *Register a Bundle ID*
> 
> 每个 iOS 应用程序都与 一个 Bundle ID 相关联，Bundle ID 是向苹果公司注册的唯一标识符。要注册应用程序的 Bundle ID，请执行以下步骤：
> 
> 1.打开开发者帐户的 App ID 页面
> 
> 2.单击+创建新的 Bundle ID
> 
> 3.输入应用程序名称，选择 `Explicit App ID`，然后输入 ID
> 
> 4.选择应用程序将使用的服务，然后单击“继续”
> 
> 5.在下一页，确认详细信息并单击 `Register ` 以注册 Bundle ID
> 
> *Create an application record on App Store Connect*
> 
> 接下来，您将在应用商店连接上注册应用程序：
> 
> 1.在浏览器中打开 App Store Connect
> 
> 2.在 App Store Connect 登录页上，单击 `My Apps`
> 
> 3.单击 `My Apps` 面左上角的“+”，然后选择 `New App`
> 
> 4.在出现的表单中填写应用程序的详细信息。在 Platforms 部分，确保选中 iOS。因为 Flutter 目前不支持 tvOS，所以不选中该复选框。单击“创建”
> 
> 5.导航到应用程序详细信息并从侧栏中选择应用程序信息
> 
> 6.在“常规信息”部分中，选择在上一步中注册的 Bundle ID
> 
> 具体参见 [App Store Connect 帮助](https://help.apple.com/app-store-connect/#/dev2cd126805)

+ Review Xcode project settings

> 在这一步中，将查看Xcode工作区中最重要的设置。有关详细步骤和说明，请参阅 [Prepare for app distribution](https://help.apple.com/xcode/mac/current/#/dev91fe7130a)
> 
> 在Xcode中导航到目标的设置：
> 
> 1.在 Xcode 中，打开应用的ios文件夹中的 Runner.xcworkspace
> 
> 2.要查看应用程序的设置，请在 Xcode 项目导航器中选择 `Runner project`。然后，在主视图侧栏中，选择 `Runner target`
> 
> 3.选择 `General` 选项卡
> 
> 在 `Identity` 部分中：
> 
> *Display Name*
> 
> 要在 `home screen` 和其他地方显示的应用程序的名称
> 
> *Bundle Identifier*
> 
> 在  App Store Connect 上注册的 App ID
> 
> 在 `Signing` 部分:
> 
> *Automatically manage signing*
> 
> Xcode 是否应自动管理应用程序签名和设置。默认设置为 true，这对于大多数应用程序来说应该足够了
> 
> *Team*
> 
> 选择与您注册的 Apple 开发者帐户关联的团队。如果需要，请选择 `Add Account…`，然后更新此设置
> 
> 在 Deployment Info 部分：
> 
> *Deployment Target*
> 
> 应用将支持的最低 iOS 版本。Flutter 支持 iOS 8.0 及更高版本。如果您的应用程序包含使用iOS 8中不可用api的 Objective-C 或 Swift 代码，请适当更新此设置

+ Updating the app’s version number

> 应用程序的默认版本号为1.0.0。要更新它，请导航到 pubspec.yaml 文件并更新以下行：

```
version: 1.0.0+1
```

> 版本号是三个由点分隔的数字，如上面示例中的1.0.0，后面是可选的内部版本号，如上面示例中的1，由+分隔
> 
> 通过分别指定 --build-name 和 --build-number，版本号和内部版本号都可以在 Flutter 的内部版本中被覆盖
> 
> 在 iOS 中，build-name 使用 CFBundleShortVersionString，而 build-number 使用 CFBundleVersion

+ Add an app icon

> 创建新的 Flutter 应用程序时，将创建一个占位符图标集。在这一步中，将用应用程序的图标替换这些占位符图标
> 
> 1.查看iOS应用图标指南
> 
> 2.在 Xcode 项目导航器中，选择 Runner 文件夹中的 Assets.xcapets。使用自己的应用程序图标更新占位符图标
> 
> 3.使用 `flutter run` 运行应用程序验证图标是否已被取代

+ Create a build archive

> 在此步骤中，将创建生成存档并将存档上载到 App Store Connect
> 
> 在开发过程中，您一直在使用调试版本进行构建、调试和测试。当你准备好将你的应用程序发布到 App Store 或 TestFlight 上的用户时，你需要准备一个发布版本
> 
> 在命令行上，在应用程序目录中执行以下步骤：
> 
> 1.运行 `flutter build ios` 以创建发布版本（ `flutter build` 默认为 `--release`）
> 
> 要确保 Xcode 刷新发布模式配置，请关闭并重新打开 Xcode 工作区。对于 Xcode 8.3 及更高版本，此步骤不是必需的
> 
> 在 Xcode 中，配置应用程序版本并生成：
> 
> 1.在 Xcode 中，打开应用的 ios 文件夹中的 `Runner.xcworkspace`
> 
> 2.选择 `Product > Scheme > Runner`
> 
> 3.选择 `Product > Destination > Generic iOS Device`
> 
> 4.在 Xcode 项目导航器中选择 Runner，然后在“设置”视图侧栏中选择 `Runner target`
> 
> 5.在 `Identity` 部分中，将版本更新为要发布的面向用户的版本号
> 
> 6.在 Identity 部分中，将 `Build identifier` 更新为用于跟踪 App Store Connect 的此生成的唯一生成号。每次上载都需要一个唯一的 build number
> 
> 最后，创建一个 build archive 并将其上载到 App Store Connect：
> 
> 1.选择 `Product > Archive` 以生成 build archive
> 
> 2.在 Xcode 管理器窗口的侧栏中，选择iOS应用程序，然后选择刚刚生成的 build archive
> 
> 3.单击 `Validate App` 按钮。如果报告了任何问题，请解决这些问题并生成另一个生成。在上载存档之前，可以重用相同的 `build ID`
> 
> 4.成功验证存档后，单击 `Distribute App`。可以在 App Store Connect 应用程序详细信息页的 `Activities` 选项卡中跟踪生成的状态
> 
> 5.您应该在30分钟内收到一封电子邮件，通知您的构建已经过验证，可以在 TestFlight 上发布给测试人员。此时，您可以选择是在 TestFlight 上发布，还是继续将应用程序发布到应用程序商店

+ Release your app on TestFlight

> TestFlight 允许开发人员将他们的应用程序推送到内部和外部测试人员那里。在这个可选步骤中，您将在 TestFlight 上发布构建
> 
> 1.导航到 App Store Connect 上 `application details` 页的 TestFlight 选项卡
> 
> 2.在侧边栏中选择 `Internal Testing`
> 
> 3.选择要发布到测试人员的 `build `，然后单击 `Save `
> 
> 4.添加任何内部测试人员的电子邮件地址。可以在 App Store Connect 的用户和角色页面中添加其他内部用户，该页面顶部的下拉菜单中提供了这些用户
> 
> 具体参见 [Distribute an app using TestFlight](https://help.apple.com/xcode/mac/current/#/dev2539d985f)

+ Release your app to the App Store

> 当您准备好向世界发布应用程序时，请按照以下步骤提交应用程序以供审阅并发布到应用程序商店：
> 
> 1.从 App Store Connect 上应用程序的详细信息页面的侧栏中选择定价和可用性，并完成所需信息
> 
> 2.从侧栏中选择状态。如果这是此应用的第一个版本，则其状态将为1.0准备提交。填写所有必需字段
> 
> 3.点击 `Submit for Review`
> 
> 苹果将在他们的应用程序审查过程完成时通知您。您的应用程序将根据您在版本发布部分中指定的说明发布
> 
> 具体参见 [Distribute an app through the App Store](https://help.apple.com/xcode/mac/current/#/dev067853c94)

## [Build and release a web app](https://flutter.dev/docs/deployment/web)

## [Continuous delivery with Flutter](https://flutter.dev/docs/deployment/cd)

+ 使用 Flutter 遵循持续交付的最佳实践，以确保您的应用程序交付给您的beta测试人员，并在不使用手动工作流的情况下频繁地进行验证

+ fastlane

> 本指南展示了如何将 fastlane（开源软件套件）与现有的测试和连续集成（CI）工作流（例如，Travis 或 Cirrus ）集成在一起
> 
> *Local setup*
> 
> 建议您在迁移到基于云的系统之前在本地测试构建和部署过程。您还可以选择从本地计算机执行连续传送
> 
> **not finished**

# Resources

## [Bootstrap into Dart](https://flutter.dev/docs/resources/bootstrap-into-dart)

## [Flutter compatibility policy](https://flutter.dev/docs/resources/compatibility)

## [Inside Flutter](https://flutter.dev/docs/resources/inside-flutter)

## [Platform specific behaviors and adaptations](https://flutter.dev/docs/resources/platform-adaptations)


---
# [*Cookbook*](https://flutter.dev/docs/cookbook)

## Animation

### [Animate a page route transition](https://flutter.dev/docs/cookbook/animation/page-route-animation)

### [Animate a widget using a physics simulation](https://flutter.dev/docs/cookbook/animation/physics-simulation)

### [Animate the properties of a container](https://flutter.dev/docs/cookbook/animation/animated-container)

### [Fade a widget in and out](https://flutter.dev/docs/cookbook/animation/opacity-animation)

## Design

### [Add a Drawer to a screen](https://flutter.dev/docs/cookbook/design/drawer)

+ 在使用 Material Design 的应用程序中，导航有两个主要选项：tab 和 drawer。当没有足够的空间来支撑 tab 时，drawer 提供了一个方便的选择

+ 在 Flutter 中，将 Drawer 小部件与 Scaffold 结合使用，创建一个具有 Material Design Drawer的布局。使用以下步骤：

> 1.创建 Scaffold
> 
> 2.添加 Drawer
> 
> 3.用项目填充 Drawer
> 
> 4.以编程方式关闭 Drawer

+ 1. Create a Scaffold

> 要向应用程序添加 Drawer，请将其包装在 Scaffold 小部件中。Scaffold 小部件为遵循 Material Design 准则的应用程序提供了一致的视觉结构。它还支持特殊的 Material Design 组件，如 Drawer、 AppBar 和 SnackBar
> 
> 在本例中，创建带 Drawer 的 Scaffold：

```
Scaffold(
  drawer: // Add a Drawer here in the next step.
);
```

+ 2. Add a drawer

> 在 Scaffold 上加一个 Drawer。Drawer 可以是任何小部件，但通常最好使用 Material 库中的 Drawer 小部件，它遵循 Material Design 规范

```
Scaffold(
  drawer: Drawer(
    child: // Populate the Drawer in the next step.
  )
);
```

+ 3. Populate the drawer with items

> 既然已经准备好了 Drawer，就给它添加内容。对于本例，请使用 ListView。虽然可以使用 Column 小部件，但 ListView 很方便，因为如果内容占用的空间超过屏幕支持的空间，它允许用户在 Drawer 中滚动
> 
> 用一个 DrawerHeader 和两个 ListTile 小部件填充 ListView

```
Drawer(
  // Add a ListView to the drawer. This ensures the user can scroll
  // through the options in the drawer if there isn't enough vertical
  // space to fit everything.
  child: ListView(
    // Important: Remove any padding from the ListView.
    padding: EdgeInsets.zero,
    children: <Widget>[
      DrawerHeader(
        child: Text('Drawer Header'),
        decoration: BoxDecoration(
          color: Colors.blue,
        ),
      ),
      ListTile(
        title: Text('Item 1'),
        onTap: () {
          // Update the state of the app.
          // ...
        },
      ),
      ListTile(
        title: Text('Item 2'),
        onTap: () {
          // Update the state of the app.
          // ...
        },
      ),
    ],
  ),
);

```


+ 4. Close the drawer programmatically

> 用户点击项目后，可能需要关闭 drawer 。您可以使用 Navigator 来完成此操作
> 
> 当用户打开 drawer 时，Flutter 会将 drawer 添加到导航堆栈中。因此，要关闭 drawer，请调用 Navigator.pop（context）

```
ListTile(
  title: Text('Item 1'),
  onTap: () {
    // Update the state of the app.
    // ...
    // Then close the drawer.
    Navigator.pop(context);
  },
),
```

+ 完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  final appTitle = 'Drawer Demo';

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: appTitle,
      home: MyHomePage(title: appTitle),
    );
  }
}

class MyHomePage extends StatelessWidget {
  final String title;

  MyHomePage({Key key, this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: Center(child: Text('My Page!')),
      drawer: Drawer(
        // Add a ListView to the drawer. This ensures the user can scroll
        // through the options in the drawer if there isn't enough vertical
        // space to fit everything.
        child: ListView(
          // Important: Remove any padding from the ListView.
          padding: EdgeInsets.zero,
          children: <Widget>[
            DrawerHeader(
              child: Text('Drawer Header'),
              decoration: BoxDecoration(
                color: Colors.blue,
              ),
            ),
            ListTile(
              title: Text('Item 1'),
              onTap: () {
                // Update the state of the app
                // ...
                // Then close the drawer
                Navigator.pop(context);
              },
            ),
            ListTile(
              title: Text('Item 2'),
              onTap: () {
                // Update the state of the app
                // ...
                // Then close the drawer
                Navigator.pop(context);
              },
            ),
          ],
        ),
      ),
    );
  }
}
```

### [Display a snackbar](https://flutter.dev/docs/cookbook/design/snackbars)

+ 当某些操作发生时，简要地通知用户是很有用的。例如，当用户刷走列表中的邮件时，可能希望通知他们该邮件已被删除。甚至可以给他们一个撤销操作的选项。在 Material Design 中，这是 SnackBar 的工作

+ 1. Create a Scaffold

> 创建遵循 Material Design 准则的应用程序时，可为应用程序提供一致的视觉结构。在本例中，在屏幕底部显示 SnackBar，而不重叠其他重要的小部件，如 `FloatingActionButton`
> 
> 来自 material 库的 Scaffold 小部件创建了这个可视化结构，并确保重要的小部件不会重叠

```
Scaffold(
  appBar: AppBar(
    title: Text('SnackBar Demo'),
  ),
  body: SnackBarPage(), // Complete this code in the next step.
);
```

+ 2. Display a SnackBar

> 在 Scaffold 就位的情况下，展示一个 SnackBar。首先，创建一个 SnackBar，然后使用 Scaffold 显示它

```
final snackBar = SnackBar(content: Text('Yay! A SnackBar!'));

// Find the Scaffold in the widget tree and use it to show a SnackBar.
Scaffold.of(context).showSnackBar(snackBar);
```

+ 3. Provide an optional action

> 可能希望在显示 SnackBar 时向用户提供操作。例如，如果用户意外地删除了一条消息，可以使用 SnackBar 中的可选操作来恢复该消息
> 
> 下面是为SnackBar小部件提供附加操作的示例：

```
final snackBar = SnackBar(
  content: Text('Yay! A SnackBar!'),
  action: SnackBarAction(
    label: 'Undo',
    onPressed: () {
      // Some code to undo the change.
    },
  ),
);
```

+ 完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(SnackBarDemo());

class SnackBarDemo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SnackBar Demo',
      home: Scaffold(
        appBar: AppBar(
          title: Text('SnackBar Demo'),
        ),
        body: SnackBarPage(),
      ),
    );
  }
}

class SnackBarPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: RaisedButton(
        onPressed: () {
          final snackBar = SnackBar(
            content: Text('Yay! A SnackBar!'),
            action: SnackBarAction(
              label: 'Undo',
              onPressed: () {
                // Some code to undo the change.
              },
            ),
          );

          // Find the Scaffold in the widget tree and use
          // it to show a SnackBar.
          Scaffold.of(context).showSnackBar(snackBar);
        },
        child: Text('Show SnackBar'),
      ),
    );
  }
}
```

### [Export fonts from a package](https://flutter.dev/docs/cookbook/design/package-fonts)

+ 可以将字体声明为单独包的一部分，而不是将字体声明为应用程序的一部分。这是一种在多个不同项目中共享相同字体的方便方法，或者对于将其包发布到 pub.dev 的程序员来说也是一种方便的方法

> 查看 google_fonts 包，可以直接访问近1000个开源字体系列

+ 1. Add a font to a package

> 要从包中导出字体，需要将字体文件导入到包项目的 lib 文件夹中。可以将字体文件直接放在 lib 文件夹或子目录中，例如 lib/fonts
> 
> 在本例中，假设您有一个名为 awesome_package 的 Flutter 库，其中的字体位于 lib/fonts 文件夹中

```
awesome_package/
  lib/
    awesome_package.dart
    fonts/
      Raleway-Regular.ttf
      Raleway-Italic.ttf
```

+ 2.Add the package and fonts to the app

> 现在可以通过更新应用程序根目录中的 pubspec.yaml 来使用包中的字体
> 
> *Add the package to the app*

```
dependencies:
  awesome_package: <latest_version>
```

> *Declare the font assets*
> 
> 既然已经导入了这个包，告诉 Flutter 在哪里可以从 awesome_package 中找到字体
> 
> 要声明包字体，请在字体的路径前面加上 packages/awesome_package。这告诉 Flutter 在包的 lib 文件夹中查找字体

```
flutter:
  fonts:
    - family: Raleway
      fonts:
        - asset: packages/awesome_package/fonts/Raleway-Regular.ttf
        - asset: packages/awesome_package/fonts/Raleway-Italic.ttf
          style: italic
```

> *3. Use the font*
> 
> 使用 TextStyle 更改文本的外观。要使用包字体，请声明要使用的字体以及该字体所属的包

```
Text(
  'Using the Raleway font from the awesome_package',
  style: TextStyle(
    fontFamily: 'Raleway',
    package: 'awesome_package',
  ),
);
```

+ 完整示例

> *Fonts*
> 
> Raleway 和 RobotoMono 字体是从 [Google fonts](https://fonts.google.com)下载的
> 
> *pubspec.yaml*

```
name: package_fonts
description: An example of how to use package fonts with Flutter

dependencies:
  awesome_package:
  flutter:
    sdk: flutter

dev_dependencies:
  flutter_test:
    sdk: flutter

flutter:
  fonts:
    - family: Raleway
      fonts:
        - asset: packages/awesome_package/fonts/Raleway-Regular.ttf
        - asset: packages/awesome_package/fonts/Raleway-Italic.ttf
          style: italic
  uses-material-design: true
```

+ *main.dart*

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Package Fonts',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // The AppBar uses the app-default font.
      appBar: AppBar(title: Text('Package Fonts')),
      body: Center(
        // This Text widget uses the Raleway font.
        child: Text(
          'Using the Raleway font from the awesome_package',
          style: TextStyle(
            fontFamily: 'Raleway',
            package: 'awesome_package',
          ),
        ),
      ),
    );
  }
}
```

### [Update the UI based on orientation](https://flutter.dev/docs/cookbook/design/orientation)

+ 在某些情况下，当用户将屏幕从纵向模式旋转到横向模式时，您需要更新应用程序的显示。例如，应用程序可能在纵向模式下显示一个项目，但在横向模式下将这些相同的项目并排显示

> 在 Flutter 中，可以根据给定的方向构建不同的布局。在本例中，使用以下步骤构建一个列表，该列表在纵向模式下显示两列，在横向模式下显示三列：
> 
> 1.生成包含两列的 GridView
> 
> 2.使用 OrientationBuilder 更改列数

+ 1. Build a GridView with two columns

> 首先，创建要使用的项列表。不要使用普通列表，而是创建一个在网格中显示项的列表。现在，创建一个包含两列的网格

```
GridView.count(
  // A list with 2 columns
  crossAxisCount: 2,
  // ...
);
```

+ 2. Use an OrientationBuilder to change the number of columns

> 要确定应用程序的当前方向，请使用 OrientationBuilder 小部件。 OrientationBuilder 通过比较父窗口小部件可用的宽度和高度来计算当前方向，并在父窗口小部件的大小更改时重建
> 
> 使用方向，构建一个列表，以纵向模式显示两列，或以横向模式显示三列

```
OrientationBuilder(
  builder: (context, orientation) {
    return GridView.count(
      // Create a grid with 2 columns in portrait mode,
      // or 3 columns in landscape mode.
      crossAxisCount: orientation == Orientation.portrait ? 2 : 3,
    );
  },
);
```

> 如果您对屏幕的方向感兴趣，而不是对父级可用的空间量感兴趣，请使用 MediaQuery.of（context）.orientation 而不是 OrientationBuilder 小部件

+ 完整例子

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final appTitle = 'Orientation Demo';

    return MaterialApp(
      title: appTitle,
      home: OrientationList(
        title: appTitle,
      ),
    );
  }
}

class OrientationList extends StatelessWidget {
  final String title;

  OrientationList({Key key, this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: OrientationBuilder(
        builder: (context, orientation) {
          return GridView.count(
            // Create a grid with 2 columns in portrait mode, or 3 columns in
            // landscape mode.
            crossAxisCount: orientation == Orientation.portrait ? 2 : 3,
            // Generate 100 widgets that display their index in the List.
            children: List.generate(100, (index) {
              return Center(
                child: Text(
                  'Item $index',
                  style: Theme.of(context).textTheme.headline,
                ),
              );
            }),
          );
        },
      ),
    );
  }
}
```

### [Use a custom font](https://flutter.dev/docs/cookbook/design/fonts)

+ 尽管 Android 和 iOS 提供了高质量的系统字体，但设计师最常见的要求之一是定制字体。例如，您可能有一个来自设计师的自定义字体，或者您可能从 Google Fonts 下载了一个字体

+ Flutter 使用自定义字体，您可以在整个应用程序或单个小部件上应用自定义字体

+ 1. Import the font files

> 要使用字体，请将字体文件导入到项目中。通常的做法是将字体文件放在 flutter 项目根目录下的 fonts 或 assets 文件夹中
> 
> 例如，要将 Raleway 和 Roboto Mono 字体文件导入到项目中，文件夹结构可能如下所示：

```
awesome_app/
  fonts/
    Raleway-Regular.ttf
    Raleway-Italic.ttf
    RobotoMono-Regular.ttf
    RobotoMono-Bold.ttf
```

+ 2. Declare the font in the pubspec

> 一旦你确定了一个字体，告诉 Flutter 在哪里找到它。可以通过在 pubspec.yaml 文件中包含字体定义来完成此操作

```
flutter:
  fonts:
    - family: Raleway
      fonts:
        - asset: fonts/Raleway-Regular.ttf
        - asset: fonts/Raleway-Italic.ttf
          style: italic
    - family: RobotoMono
      fonts:
        - asset: fonts/RobotoMono-Regular.ttf
        - asset: fonts/RobotoMono-Bold.ttf
          weight: 700
```

> *pubspec.yaml option definitions*
> 
> family 决定字体的名称，可以在 TextStyle 对象的 fontFamily 属性中使用该字体
> 
> asset 是相对于 pubspec.yaml 文件的字体文件的路径。这些文件包含字体中字形的轮廓。构建应用程序时，这些文件包含在应用程序的 asset bundle 中
> 
> 单个字体可以引用具有不同轮廓权重和样式的许多不同文件：
> 
> weight 属性将文件中轮廓的权重指定为100的整数倍，介于100和900之间。这些值对应于 FontWeight，可以在 TextStyle 对象的 FontWeight 属性中使用
> 
> style 属性指定文件中的轮廓是 italic 还是 normal。这些值与 FontStyle 相对应，可以在 TextStyle 对象的 FontStyle 属性中使用

+ 3. Set a font as the default

> 对于如何将字体应用于文本，有两个选项：作为默认字体或仅在特定小部件中
> 
> 若要将字体用作默认字体，请将 fontFamily 属性设置为应用程序主题的一部分。提供给 fontFamily 的值必须与 pubspec.yaml 中声明的家族名称匹配

```
MaterialApp(
  title: 'Custom Fonts',
  // Set Raleway as the default app font.
  theme: ThemeData(fontFamily: 'Raleway'),
  home: MyHomePage(),
);
```

+ 4. Use the font in a specific widget

> 如果要将字体应用于特定小部件（如 Text 小部件），请为该小部件提供文本样式
> 
> 在本例中，将 RobotoMono 字体应用于单个 Text 小部件。 fontFamily 必须再次与 pubspec.yaml 中声明的名称匹配

```
Text(
  'Roboto Mono sample',
  style: TextStyle(fontFamily: 'RobotoMono'),
);
```

> 如果 TextStyle 对象指定了没有确切字体文件的权重或样式，则引擎将使用一个更通用的字体文件，并尝试为请求的权重和样式外推轮廓

+ 完整例子

> pubspec.yaml

```
name: custom_fonts
description: An example of how to use custom fonts with Flutter

dependencies:
  flutter:
    sdk: flutter

dev_dependencies:
  flutter_test:
    sdk: flutter

flutter:
  fonts:
    - family: Raleway
      fonts:
        - asset: fonts/Raleway-Regular.ttf
        - asset: fonts/Raleway-Italic.ttf
          style: italic
    - family: RobotoMono
      fonts:
        - asset: fonts/RobotoMono-Regular.ttf
        - asset: fonts/RobotoMono-Bold.ttf
          weight: 700
  uses-material-design: true

```

> main.dart

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Custom Fonts',
      // Set Raleway as the default app font.
      theme: ThemeData(fontFamily: 'Raleway'),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // The AppBar uses the app-default Raleway font.
      appBar: AppBar(title: Text('Custom Fonts')),
      body: Center(
        // This Text widget uses the RobotoMono font.
        child: Text(
          'Roboto Mono sample',
          style: TextStyle(fontFamily: 'RobotoMono'),
        ),
      ),
    );
  }
}

```

### [Use themes to share colors and font styles](https://flutter.dev/docs/cookbook/design/themes)

+ 要在应用程序中共享颜色和字体样式，请使用主题。可以定义应用程序范围的主题，也可以使用主题小部件来定义应用程序特定部分的颜色和字体样式。实际上，应用程序范围的主题只是MaterialApp在应用程序根目录下创建的主题小部件

+ 定义主题后，在自己的小部件中使用它。Flutter 的Material widgets还使用您的主题设置appbar、按钮、复选框等的背景颜色和字体样式

+ Creating an app theme

> 要在整个应用程序中共享主题，请向 MaterialApp 构造函数提供主题数据
> 
> 如果没有提供主题，Flutter 会创建一个默认主题

```
MaterialApp(
  title: title,
  theme: ThemeData(
    // Define the default brightness and colors.
    brightness: Brightness.dark,
    primaryColor: Colors.lightBlue[800],
    accentColor: Colors.cyan[600],

    // Define the default font family.
    fontFamily: 'Georgia',

    // Define the default TextTheme. Use this to specify the default
    // text styling for headlines, titles, bodies of text, and more.
    textTheme: TextTheme(
      headline: TextStyle(fontSize: 72.0, fontWeight: FontWeight.bold),
      title: TextStyle(fontSize: 36.0, fontStyle: FontStyle.italic),
      body1: TextStyle(fontSize: 14.0, fontFamily: 'Hind'),
    ),
  )
);

```

+ Themes for part of an application

> 要在应用程序的一部分覆盖应用程序范围的主题，请在主题小部件中包装应用程序的一部分
> 
> 有两种方法可以实现此目的：创建唯一的 ThemeData，或扩展父主题
> 
> *Creating unique ThemeData*
> 
> 如果不想继承任何应用程序颜色或字体样式，请创建一个 ThemeData（）实例并将其传递给 Theme 小部件

```
Theme(
  // Create a unique theme with "ThemeData"
  data: ThemeData(
    accentColor: Colors.yellow,
  ),
  child: FloatingActionButton(
    onPressed: () {},
    child: Icon(Icons.add),
  ),
);

```

> *Extending the parent theme*
> 
> 与其覆盖所有内容，不如扩展父主题。您可以使用copyWith（）方法来处理这个问题

```
Theme(
  // Find and extend the parent theme using "copyWith". See the next
  // section for more info on `Theme.of`.
  data: Theme.of(context).copyWith(accentColor: Colors.yellow),
  child: FloatingActionButton(
    onPressed: null,
    child: Icon(Icons.add),
  ),
);

```

+ Using a Theme

> 既然已经定义了一个主题，那么通过使用 Theme.of（context）方法在小部件的build（）方法中使用它
> 
> Theme.of（context）方法查找小部件树并返回树中最近的主题。如果在小部件上方定义了独立主题，则返回该主题。如果没有，则返回应用程序的主题
> 
> 实际上，FloatingActionButton 使用这种技术来查找 accentColor

```
Container(
  color: Theme.of(context).accentColor,
  child: Text(
    'Text with a background color',
    style: Theme.of(context).textTheme.title,
  ),
);
```

+ 完整例子

```
import 'package:flutter/foundation.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final appName = 'Custom Themes';

    return MaterialApp(
      title: appName,
      theme: ThemeData(
        // Define the default brightness and colors.
        brightness: Brightness.dark,
        primaryColor: Colors.lightBlue[800],
        accentColor: Colors.cyan[600],

        // Define the default font family.
        fontFamily: 'Georgia',

        // Define the default TextTheme. Use this to specify the default
        // text styling for headlines, titles, bodies of text, and more.
        textTheme: TextTheme(
          headline: TextStyle(fontSize: 72.0, fontWeight: FontWeight.bold),
          title: TextStyle(fontSize: 36.0, fontStyle: FontStyle.italic),
          body1: TextStyle(fontSize: 14.0, fontFamily: 'Hind'),
        ),
      ),
      home: MyHomePage(
        title: appName,
      ),
    );
  }
}

class MyHomePage extends StatelessWidget {
  final String title;

  MyHomePage({Key key, @required this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: Container(
          color: Theme.of(context).accentColor,
          child: Text(
            'Text with a background color',
            style: Theme.of(context).textTheme.title,
          ),
        ),
      ),
      floatingActionButton: Theme(
        data: Theme.of(context).copyWith(
          colorScheme:
              Theme.of(context).colorScheme.copyWith(secondary: Colors.yellow),
        ),
        child: FloatingActionButton(
          onPressed: null,
          child: Icon(Icons.add),
        ),
      ),
    );
  }
}
```

### [Work with tabs](https://flutter.dev/docs/cookbook/design/tabs)

+ 在遵循 Material Design 指南的应用程序中，使用 tab 是一种常见的模式。Flutter 包含一种方便的方法，可以将选项卡布局创建为 material 库的一部分

+ 1. Create a TabController

> 要使 tab 正常工作，需要使选定的 tab 和内容节保持同步。这是 TabController 的工作
> 
> 手动创建 TabController，或者使用 DefaultTabController 小部件自动创建 TabController
> 
> 使用 DefaultTabController 是最简单的选项，因为它创建了一个 TabController 并使其对所有子代小部件都可用

```
DefaultTabController(
  // The number of tabs / content sections to display.
  length: 3,
  child: // Complete this code in the next step.
);
```

+ 2. Create the tabs

> 选择 tab 时，它需要显示内容。可以使用 TabBar 小部件创建 tab。在本例中，创建一个包含三个 tab 小部件的 TabBar，并将其放置在 AppBar 中

```
DefaultTabController(
  length: 3,
  child: Scaffold(
    appBar: AppBar(
      bottom: TabBar(
        tabs: [
          Tab(icon: Icon(Icons.directions_car)),
          Tab(icon: Icon(Icons.directions_transit)),
          Tab(icon: Icon(Icons.directions_bike)),
        ],
      ),
    ),
  ),
);
```

> 默认情况下，TabBar 会在小部件树中查找最近的 DefaultTabController。如果要手动创建 TabController，请将其传递给 TabBar

+ 3. Create content for each tab

> 现在你有Tabs，当选定Tab时显示内容。为了这个目的，使用Tabbarview Widget
> 
> 顺序很重要，必须与 TabBar 中 tab 的顺序相对应

```
TabBarView(
  children: [
    Icon(Icons.directions_car),
    Icon(Icons.directions_transit),
    Icon(Icons.directions_bike),
  ],
);
```

+ 完整例子

```
import 'package:flutter/material.dart';

void main() {
  runApp(TabBarDemo());
}

class TabBarDemo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DefaultTabController(
        length: 3,
        child: Scaffold(
          appBar: AppBar(
            bottom: TabBar(
              tabs: [
                Tab(icon: Icon(Icons.directions_car)),
                Tab(icon: Icon(Icons.directions_transit)),
                Tab(icon: Icon(Icons.directions_bike)),
              ],
            ),
            title: Text('Tabs Demo'),
          ),
          body: TabBarView(
            children: [
              Icon(Icons.directions_car),
              Icon(Icons.directions_transit),
              Icon(Icons.directions_bike),
            ],
          ),
        ),
      ),
    );
  }
}
```

## Forms

### [Build a form with validation](https://flutter.dev/docs/cookbook/forms/validation)

+ 应用程序通常要求用户在文本字段中输入信息。例如，可能要求用户使用电子邮件地址和密码组合登录

+ 要使应用程序安全且易于使用，请检查用户提供的信息是否有效。如果用户正确填写了表单，请处理该信息。如果用户提交的信息不正确，则显示友好的错误消息，让他们知道发生了什么错误

+ 在本例中，学习如何使用以下步骤将验证添加到具有单个文本字段的表单：

> 1.使用 GlobalKey 创建窗体
> 
> 2.添加带有验证逻辑的 TextFormField
> 
> 3.创建一个按钮来验证和提交表单

+ 1. Create a Form with a GlobalKey

> 首先，创建一个表单。表单小部件充当对多个表单字段进行分组和验证的容器
> 
> 创建窗体时，提供 GlobalKey。这唯一地标识表单，并允许在以后的步骤中验证表单

```
// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  MyCustomFormState createState() {
    return MyCustomFormState();
  }
}

// Define a corresponding State class.
// This class holds data related to the form.
class MyCustomFormState extends State<MyCustomForm> {
  // Create a global key that uniquely identifies the Form widget
  // and allows validation of the form.
  //
  // Note: This is a `GlobalKey<FormState>`,
  // not a GlobalKey<MyCustomFormState>.
  final _formKey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
    // Build a Form widget using the _formKey created above.
    return Form(
      key: _formKey,
      child: Column(
        children: <Widget>[
              // Add TextFormFields and RaisedButton here.
        ]
     )
    );
  }
}
```

> 使用 GlobalKey 是访问表单的推荐方法。但是，如果有更复杂的小部件树，则可以使用Form.of（）方法在嵌套的小部件中访问表单

+ 2. Add a TextFormField with validation logic

> 尽管表单已经就位，但它没有让用户输入文本的方法。这是 TextFormField 的工作。 TextFormField 小部件呈现一个 material design 文本字段，并在出现验证错误时显示这些错误
> 
> 通过向 TextFormField 提供 validator（）函数来验证输入。如果用户的输入无效，验证函数将返回包含错误消息的字符串。如果没有错误，验证程序必须返回 null
> 
> 对于本例，创建一个 validator，确保 TextFormField 不为空。如果为空，则返回友好的错误消息

```
TextFormField(
  // The validator receives the text that the user has entered.
  validator: (value) {
    if (value.isEmpty) {
      return 'Please enter some text';
    }
    return null;
  },
);
```

+ 3. Create a button to validate and submit the form

> 现在您有了一个带有文本字段的表单，请提供一个按钮，用户可以点击该按钮提交信息
> 
> 当用户试图提交表单时，请检查表单是否有效。如果是，则显示一条成功消息。如果不是（文本字段没有内容），则显示错误消息

```
RaisedButton(
  onPressed: () {
    // Validate returns true if the form is valid, otherwise false.
    if (_formKey.currentState.validate()) {
      // If the form is valid, display a snackbar. In the real world,
      // you'd often call a server or save the information in a database.

      Scaffold
          .of(context)
          .showSnackBar(SnackBar(content: Text('Processing Data')));
    }
  },
  child: Text('Submit'),
);
```

+ How does this work?

> 要验证表单，请使用步骤1中创建的 _formKey。可以使用 _formKey.currentState（）方法访问 FormState，它是在生成表单时由 Flutter 自动创建的
> 
> FormState 类包含 validate（）方法。调用 validate（）方法时，它为表单中的每个文本字段运行 validator（）函数。如果一切正常，validate（）方法返回 true。如果任何文本字段包含错误，validate（）方法将重建窗体以显示任何错误消息并返回 false

+ 完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final appTitle = 'Form Validation Demo';

    return MaterialApp(
      title: appTitle,
      home: Scaffold(
        appBar: AppBar(
          title: Text(appTitle),
        ),
        body: MyCustomForm(),
      ),
    );
  }
}

// Create a Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  MyCustomFormState createState() {
    return MyCustomFormState();
  }
}

// Create a corresponding State class.
// This class holds data related to the form.
class MyCustomFormState extends State<MyCustomForm> {
  // Create a global key that uniquely identifies the Form widget
  // and allows validation of the form.
  //
  // Note: This is a GlobalKey<FormState>,
  // not a GlobalKey<MyCustomFormState>.
  final _formKey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
    // Build a Form widget using the _formKey created above.
    return Form(
      key: _formKey,
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: <Widget>[
          TextFormField(
            validator: (value) {
              if (value.isEmpty) {
                return 'Please enter some text';
              }
              return null;
            },
          ),
          Padding(
            padding: const EdgeInsets.symmetric(vertical: 16.0),
            child: RaisedButton(
              onPressed: () {
                // Validate returns true if the form is valid, or false
                // otherwise.
                if (_formKey.currentState.validate()) {
                  // If the form is valid, display a Snackbar.
                  Scaffold.of(context)
                      .showSnackBar(SnackBar(content: Text('Processing Data')));
                }
              },
              child: Text('Submit'),
            ),
          ),
        ],
      ),
    );
  }
}
```

### [Create and style a text field](https://flutter.dev/docs/cookbook/forms/text-input)

+ Text 字段允许用户在应用程序中键入文本。它们用于构建表单、发送消息、创建搜索体验等

+ Flutter 提供两个文本字段：TextField 和 TextFormField

+ TextField

> TextField 是最常用的文本输入小部件
> 
> 默认情况下，文本字段用下划线修饰。通过提供 InputDecoration 作为文本字段的装饰属性，可以添加标签、图标、内联提示文本和错误文本。若要完全删除装饰（包括下划线和为标签保留的空间），请将装饰设置为空

```
TextField(
  decoration: InputDecoration(
    border: InputBorder.none,
    hintText: 'Enter a search term'
  ),
);
```

+ TextFormField

> TextFormField 包装一个 TextField 并将其与封闭表单集成。这提供了额外的功能，例如验证和与其他 FormField 小部件的集成

```
TextFormField(
  decoration: InputDecoration(
    labelText: 'Enter your username'
  ),
);
```

### [Focus and text fields](https://flutter.dev/docs/cookbook/forms/focus)

+ 当选择一个文本字段并接受输入时，它被称为具有“焦点”。通常，用户通过点击将焦点转移到文本字段，开发人员通过使用本节描述的工具以编程方式将焦点转移到文本字段

+ 管理焦点是创建具有直观流的表单的基本工具。例如，假设您有一个带有文本字段的搜索屏幕。当用户导航到搜索屏幕时，可以将焦点设置为搜索词的文本字段。这允许用户在屏幕可见时立即开始键入，而无需手动点击文本字段

+ 在本节中，学习如何在文本字段可见时立即将焦点赋予文本字段，以及如何在点击按钮时将焦点赋予文本字段

+ Focus a text field as soon as it’s visible

> 若要在文本字段可见时立即为其提供焦点，请使用“autofocus”属性

```
TextField(
  autofocus: true,
);
```

+ Focus a text field when a button is tapped

> 与其立即将焦点转移到特定的文本字段，不如在稍后的时间点将焦点转移到文本字段。在现实世界中，您可能还需要将焦点放在特定的文本字段上，以响应 API 调用或验证错误。在本例中，在用户按下按钮后，使用以下步骤将焦点放在文本字段上：
> 
> *1. Create a FocusNode*
> 
> 首先，创建一个 FocusNode。使用 FocusNode 来识别 Flutter 的“焦点树”中的一个特定文本字段，这允许您在接下来的步骤中对文本字段进行聚焦
> 
> 由于 FocusMode 是长寿命对象，因此使用状态对象管理生命周期。使用以下说明在状态类的 initState（）方法中创建 FocusMode 实例，并在 dispose（）方法中清除它：

```
// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds data related to the form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Define the focus node. To manage the lifecycle, create the FocusNode in
  // the initState method, and clean it up in the dispose method.
  FocusNode myFocusNode;

  @override
  void initState() {
    super.initState();

    myFocusNode = FocusNode();
  }

  @override
  void dispose() {
    // Clean up the focus node when the Form is disposed.
    myFocusNode.dispose();

    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    // Fill this out in the next step.
  }
}
```

> *2. Pass the FocusNode to a TextField*
> 
> 现在有了 FocusNode，请将其传递给 build（）方法中的特定 TextField

```
class _MyCustomFormState extends State<MyCustomForm> {
  // Code to create the Focus node...

  @override
  Widget build(BuildContext context) {
    return TextField(
      focusNode: myFocusNode,
    );
  }
}
```

> *3. Give focus to the TextField when a button is tapped*
> 
> 最后，当用户点击一个浮动操作按钮时，聚焦文本字段。使用 requestFocus（）方法执行此任务

```
FloatingActionButton(
  // When the button is pressed, give focus to the text field using
  // myFocusNode.
  onPressed: () => FocusScope.of(context).requestFocus(myFocusNode),
);
```

+  完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Text Field Focus',
      home: MyCustomForm(),
    );
  }
}

// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds data related to the form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Define the focus node. To manage the lifecycle, create the FocusNode in
  // the initState method, and clean it up in the dispose method.
  FocusNode myFocusNode;

  @override
  void initState() {
    super.initState();

    myFocusNode = FocusNode();
  }

  @override
  void dispose() {
    // Clean up the focus node when the Form is disposed.
    myFocusNode.dispose();

    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Text Field Focus'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            // The first text field is focused on as soon as the app starts.
            TextField(
              autofocus: true,
            ),
            // The second text field is focused on when a user taps the
            // FloatingActionButton.
            TextField(
              focusNode: myFocusNode,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        // When the button is pressed,
        // give focus to the text field using myFocusNode.
        onPressed: () => FocusScope.of(context).requestFocus(myFocusNode),
        tooltip: 'Focus Second Text Field',
        child: Icon(Icons.edit),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```

### [Handle changes to a text field](https://flutter.dev/docs/cookbook/forms/text-field-changes)

+ 在某些情况下，每次文本字段中的文本更改时运行回调函数是很有用的。例如，您可能希望构建一个具有自动完成功能的搜索屏幕，以便在用户键入时更新结果

+ 如何在每次文本更改时运行回调函数？有两个选择：

> *1. Supply an onChanged() callback to a TextField or a TextFormField*
> 
> 最简单的方法是向 TextField 或 TextFormField 提供 onChanged（）回调。每当文本更改时，都会调用回调
> 
> 在本例中，每次文本更改时都将文本字段的当前值打印到控制台

```
TextField(
  onChanged: (text) {
    print("First text field: $text");
  },
);
```

> *2. Use a TextEditingController*
> 
> 一种更强大但更精细的方法是提供 TextEditingController 作为 TextField 或 TextFormField的controller 属性
> 
> **Create a TextEditingController**

```
// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds data related to the Form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Create a text controller. Later, use it to retrieve the
  // current value of the TextField.
  final myController = TextEditingController();

  @override
  void dispose() {
    // Clean up the controller when the widget is removed from the
    // widget tree.
    myController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    // Fill this out in the next step.
  }
}

```

> 当不再需要 TextEditingController 时，请记住将其释放。这样可以确保释放对象使用的任何资源
> 
> **Connect the TextEditingController to a text field**
> 
> 为 TextField 或 TextFormField 提供 TextEditingController 。一旦将这两个类连接在一起，就可以开始侦听对文本字段的更改

```
TextField(
  controller: myController,
);
```

> **Create a function to print the latest value**
> 
> 每次文本更改时都需要运行一个函数。在 MyCustomFormState 类中创建一个方法，打印出文本字段的当前值

```
每次文本更改时都需要运行一个函数。在MyCustomFormState类中创建一个方法，打印出文本字段的当前值
```

> **Listen to the controller for changes**
> 
> 最后，监听 TextEditingController 并在文本更改时调用 _printLatestValue（）方法。为此，请使用 addListener（）方法
> 
> 初始化 MyCustomFormState 类时开始侦听更改，释放 MyCustomFormState 时停止侦听

```
class _MyCustomFormState extends State<MyCustomForm> {
  @override
  void initState() {
    super.initState();

    // Start listening to changes.
    myController.addListener(_printLatestValue);
  }
}
```

+ 完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Retrieve Text Input',
      home: MyCustomForm(),
    );
  }
}

// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds data related to the Form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Create a text controller and use it to retrieve the current value
  // of the TextField.
  final myController = TextEditingController();

  @override
  void initState() {
    super.initState();

    myController.addListener(_printLatestValue);
  }

  @override
  void dispose() {
    // Clean up the controller when the widget is removed from the widget tree.
    // This also removes the _printLatestValue listener.
    myController.dispose();
    super.dispose();
  }

  _printLatestValue() {
    print("Second text field: ${myController.text}");
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Retrieve Text Input'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: <Widget>[
            TextField(
              onChanged: (text) {
                print("First text field: $text");
              },
            ),
            TextField(
              controller: myController,
            ),
          ],
        ),
      ),
    );
  }
}
```

### [Retrieve the value of a text field](https://flutter.dev/docs/cookbook/forms/retrieve-input)

+ 在本节中，学习如何使用以下步骤检索用户输入到文本字段中的文本：

+ 1. Create a TextEditingController

> 要检索用户在文本字段中输入的文本，请创建 TextEditingController 并将其提供给 TextField 或 TextFormField
> 
> 使用完 TextEditingController 后调用 dispose。这样可以确保放弃对象使用的任何资源

```
// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds the data related to the Form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Create a text controller and use it to retrieve the current value
  // of the TextField.
  final myController = TextEditingController();

  @override
  void dispose() {
    // Clean up the controller when the widget is disposed.
    myController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    // Fill this out in the next step.
  }
}
```

+ 2. Supply the TextEditingController to a TextField

> 有了 TextEditingController，使用 controller 属性将其连接到文本字段：

```
TextField(
  controller: myController,
);
```

+ 3. Display the current value of the text field

> 将 TextEditingController 提供给文本字段后，开始读取值。使用 TextEditingController 提供的 text（）方法检索用户在文本字段中输入的字符串
> 
> 当用户点击一个浮动操作按钮时，下面的代码显示一个带有文本字段当前值的警告对话框

```
FloatingActionButton(
  // When the user presses the button, show an alert dialog containing the
  // text that the user has entered into the text field.
  onPressed: () {
    return showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          // Retrieve the text the user has entered by using the
          // TextEditingController.
          content: Text(myController.text),
        );
      },
    );
  },
  tooltip: 'Show me the value!',
  child: Icon(Icons.text_fields),
);
```

+ 完整例子

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Retrieve Text Input',
      home: MyCustomForm(),
    );
  }
}

// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  _MyCustomFormState createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds the data related to the Form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Create a text controller and use it to retrieve the current value
  // of the TextField.
  final myController = TextEditingController();

  @override
  void dispose() {
    // Clean up the controller when the widget is disposed.
    myController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Retrieve Text Input'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: TextField(
          controller: myController,
        ),
      ),
      floatingActionButton: FloatingActionButton(
        // When the user presses the button, show an alert dialog containing
        // the text that the user has entered into the text field.
        onPressed: () {
          return showDialog(
            context: context,
            builder: (context) {
              return AlertDialog(
                // Retrieve the text the that user has entered by using the
                // TextEditingController.
                content: Text(myController.text),
              );
            },
          );
        },
        tooltip: 'Show me the value!',
        child: Icon(Icons.text_fields),
      ),
    );
  }
}
```

## Gestures

### [Add Material touch ripples](https://flutter.dev/docs/cookbook/gestures/ripples)

### [Handle taps](https://flutter.dev/docs/cookbook/gestures/handling-taps)

### [Implement swipe to dismiss](https://flutter.dev/docs/cookbook/gestures/dismissible)

## Images

### [Display images from the internet](https://flutter.dev/docs/cookbook/images/network-image)

### [Fade in images with a placeholder](https://flutter.dev/docs/cookbook/images/fading-in-images)

### [Work with cached images](https://flutter.dev/docs/cookbook/images/cached-images)

## Lists

### [Create a grid list](https://flutter.dev/docs/cookbook/lists/grid-lists)

### [Create a horizontal list](https://flutter.dev/docs/cookbook/lists/horizontal-list)

### [Create lists with different types of items](https://flutter.dev/docs/cookbook/lists/mixed-list)

### [Place a floating app bar above a list](https://flutter.dev/docs/cookbook/lists/floating-app-bar)

### [Use lists](https://flutter.dev/docs/cookbook/lists/basic-list)

### [Work with long lists](https://flutter.dev/docs/cookbook/lists/long-lists)

## Maintenance

### [Report errors to a service](https://flutter.dev/docs/cookbook/maintenance/error-reporting)

## Navigation

### [Animate a widget across screens](https://flutter.dev/docs/cookbook/navigation/hero-animations)

### [Navigate to a new screen and back](https://flutter.dev/docs/cookbook/navigation/navigation-basics)

### [Navigate with named routes](https://flutter.dev/docs/cookbook/navigation/named-routes)

### [Pass arguments to a named route](https://flutter.dev/docs/cookbook/navigation/navigate-with-arguments)

### [Return data from a screen](https://flutter.dev/docs/cookbook/navigation/returning-data)

### [Send data to a new screen](https://flutter.dev/docs/cookbook/navigation/passing-data)

## Networking

### [Fetch data from the internet](https://flutter.dev/docs/cookbook/networking/fetch-data)

### [Make authenticated requests](https://flutter.dev/docs/cookbook/networking/authenticated-requests)

### [Parse JSON in the background](https://flutter.dev/docs/cookbook/networking/background-parsing)

### [Work with WebSockets](https://flutter.dev/docs/cookbook/networking/web-sockets)

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

## Plugins

### [Play and pause a video](https://flutter.dev/docs/cookbook/plugins/play-video)

### [https://flutter.dev/docs/cookbook/plugins/picture-using-camera](Take a picture using the camera)

## Testing

### Integration

#### [An introduction to integration testing](https://flutter.dev/docs/cookbook/testing/integration/introduction)

#### [Handle scrolling](https://flutter.dev/docs/cookbook/testing/integration/scrolling)

#### [Performance profiling](https://flutter.dev/docs/cookbook/testing/integration/profiling)

### Unit

#### [An introduction to unit testing](https://flutter.dev/docs/cookbook/testing/unit/introduction)

#### [Mock dependencies using Mockito](https://flutter.dev/docs/cookbook/testing/unit/mocking)

### Widget

#### [An introduction to widget testing](https://flutter.dev/docs/cookbook/testing/widget/introduction)

#### [Find widgets](https://flutter.dev/docs/cookbook/testing/widget/finders)

#### [Tap, drag, and enter text](https://flutter.dev/docs/cookbook/testing/widget/tap-drag.html)

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
