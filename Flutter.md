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

### [Load sequence, performance, and memory](https://flutter.dev/docs/development/add-to-app/performance)

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

#### [Flutter SDK releases](https://flutter.dev/docs/development/tools/sdk/releases)

#### [Breaking changes](https://flutter.dev/docs/release/breaking-changes)

#### [Flutter release notes](https://flutter.dev/docs/development/tools/sdk/release-notes)

### [Hot reload](https://flutter.dev/docs/development/tools/hot-reload)

### [Code formatting](https://flutter.dev/docs/development/tools/formatting)

## [AndroidX Migration](https://flutter.dev/docs/development/androidx-migration)

# Testing & debugging

## [Debugging Flutter apps](https://flutter.dev/docs/testing/debugging)

## [Debugging Flutter apps programmatically](https://flutter.dev/docs/testing/code-debugging)

## [Using an OEM debugger](https://flutter.dev/docs/testing/oem-debuggers)

## [Flutter's build modes](https://flutter.dev/docs/testing/build-modes)

## [Handling errors in Flutter](https://flutter.dev/docs/testing/errors)

## [Testing Flutter apps](https://flutter.dev/docs/testing)

# Performance & optimization

## [Performance](https://flutter.dev/docs/perf)

## [Measuring your app's size](https://flutter.dev/docs/perf/app-size)

## Rendering performance

### [Improving rendering performance](https://flutter.dev/docs/perf/rendering)

### [Performance best practices](https://flutter.dev/docs/perf/rendering/best-practices)

### [Flutter performance profiling](https://flutter.dev/docs/perf/rendering/ui-performance)

# Deployment

## [Creating flavors for Flutter](https://flutter.dev/docs/deployment/flavors)

## [Build and release an Android app](https://flutter.dev/docs/deployment/android)

## [Build and release an iOS app](https://flutter.dev/docs/deployment/ios)

## [Build and release a web app](https://flutter.dev/docs/deployment/web)

## [Continuous delivery with Flutter](https://flutter.dev/docs/deployment/cd)

# Resources

## [Bootstrap into Dart](https://flutter.dev/docs/resources/bootstrap-into-dart)

## [Flutter compatibility policy](https://flutter.dev/docs/resources/compatibility)

## [Inside Flutter](https://flutter.dev/docs/resources/inside-flutter)

## [Platform specific behaviors and adaptations](https://flutter.dev/docs/resources/platform-adaptations)


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
