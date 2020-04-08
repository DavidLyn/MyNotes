---
# 概述

## 特别有用的参考资料

+ [awesome-flutter](https://github.com/Solido/awesome-flutter)

+ [一个很棒的Flutter学习资源列表](https://blog.csdn.net/sinat_17775997/article/details/82835143?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)

+ [Material icons 全图标一览](https://blog.csdn.net/boywcx/article/details/85051967)

+ [Flutter实战](https://book.flutterchina.club)

> 因为 https://material.io/resources/icons/?style=baseline 太难打开，所有才访问上述预览页面
> 
> 可使用页面上的 icon 名称在 icons.dart 中查找可用图标

+ [Flare 动画](https://www.2dimensions.com )

> user name : weiwei.lv@its.cn
> 
> password : Pass****

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

## flutter 生命周期???

+ 参考资料

> [Flutter - 生命周期](https://www.cnblogs.com/shsuper/archive/2019/09/26/11593542.html)
> 
> [Flutter 的生命周期](https://blog.csdn.net/sinat_17775997/article/details/94733411)

## fluro 路由搭建 ???

+ 参考资料

> [Flutter中fluro使用](https://www.jianshu.com/p/e575787d173c)
> 
> [theyakka/fluro](https://github.com/theyakka/fluro)
> 
> [对Flutter路由管理库Fluro的封装](https://www.wandouip.com/t5i418363/) - 此代码值得借鉴
> 
> [Flutter入门之（fluro路由跳转框架)](https://www.jianshu.com/p/1987cc9b714a) - 提供了 fluro 的路由跳转工具类，值得借鉴

## jpush_flutter 极光推送 ???


## flutter_webview_plugin 接 webview

## SQLite flutter plugin

+ [SQLite flutter plugin](https://github.com/tekartik/sqflite)


## Zefyr 富文本编辑器

+ [Zefyr](https://github.com/memspace/zefyr)


---
# 延伸技术点

## dio

+ 参考资料

> [dio/README-ZH.md](https://github.com/flutterchina/dio/blob/master/README-ZH.md)

+ dio_cookie_manager

> [dio/plugins/cookie_manager](https://github.com/flutterchina/dio/tree/master/plugins/cookie_manager)


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

+ 参考：[README_CN.md](https://github.com/peng8350/flutter_pulltorefresh/blob/master/README_CN.md) 或 [pull_to_refresh 1.5.8](https://pub.dev/packages/pull_to_refresh)

+ 全局配置 RefreshConfiguration,配置子树下的所有 SmartRefresher 表现,一般存放于 MaterialApp 的根部,用法和 ScrollConfiguration 是类似的。 另外,假如你某一个 SmartRefresher 表现和全局不一样的情况,你可以使用 RefreshConfiguration.copyAncestor 从祖先 RefreshConfiguration 复制属性过来并替换不为空的属性

```
    // 全局配置子树下的SmartRefresher,下面列举几个特别重要的属性
     RefreshConfiguration(
         headerBuilder: () => WaterDropHeader(),        // 配置默认头部指示器,假如你每个页面的头部指示器都一样的话,你需要设置这个
         footerBuilder:  () => ClassicFooter(),        // 配置默认底部指示器
         headerTriggerDistance: 80.0,        // 头部触发刷新的越界距离
         springDescription:SpringDescription(stiffness: 170, damping: 16, mass: 1.9),         // 自定义回弹动画,三个属性值意义请查询flutter api
         maxOverScrollExtent :100, //头部最大可以拖动的范围,如果发生冲出视图范围区域,请设置这个属性
         maxUnderScrollExtent:0, // 底部最大可以拖动的范围
         enableScrollWhenRefreshCompleted: true, //这个属性不兼容PageView和TabBarView,如果你特别需要TabBarView左右滑动,你需要把它设置为true
         enableLoadingWhenFailed : true, //在加载失败的状态下,用户仍然可以通过手势上拉来触发加载更多
         hideFooterWhenNotFull: false, // Viewport不满一屏时,禁用上拉加载更多功能
         enableBallisticLoad: true, // 可以通过惯性滑动触发加载更多
        child: MaterialApp(
            ........
        )
    );
```

+ 1.5.6新增国际化处理特性,你可以在MaterialApp或者CupertinoApp追加如下代码:

```
    MaterialApp(
            localizationsDelegates: [
              // 这行是关键
              RefreshLocalizations.delegate,
              GlobalWidgetsLocalizations.delegate,
              GlobalMaterialLocalizations.delegate
            ],
            supportedLocales: [
              const Locale('en'),
              const Locale('zh'),
            ],
            localeResolutionCallback:
                (Locale locale, Iterable<Locale> supportedLocales) {
              //print("change language");
              return locale;
            },
    )
```

## 状态管理 Provider

+ 比较好的参考资料：[Flutter 状态管理指南之 Provider](https://zhuanlan.zhihu.com/p/70280813?from_voters_page=true)

+ Provider 的目标就是完全替代 StatefulWidget

### ChangeNotifierProxyProvider

+ 参考资料

> [Flutter状态管理 ChangeNotifierProxyProvider的使用](https://www.jianshu.com/p/a889333d0c66)


## 国际化插件 Flutter i18n

+ 参考

> [Flutter-国际化适配终结者](https://juejin.im/post/5c701379f265da2d9b5e196a#heading-1)
> 
> [Flutter i18n官网](https://github.com/long1eu/flutter_i18n)

+ 在 Android Studio 中安装插件

> 菜单 : [Android Studio] -> [Preferences] -> [Plugins] -> 
> 
> 然后点击插件列表下面的 `Browe repositories`,然后在弹出的界面中输入 `Flutter i18n`

+ **可能是在 Android Studio 中只能安装版本很低的插件，生成的 i18n.dart 文件与原有文件差异较大，且存在编译错误，无奈由将该插件卸载，且恢复 i18n.dart 后，才能正常编译**

## 路由和导航

+ 参考 : [Flutter 路由和导航](https://www.jianshu.com/p/3b105658728e)

+ 使用 PageRouteBuilder 自定义路由

> 参考 : [关于 Flutter 页面路由过渡动画，你所需要知道的一切](https://blog.csdn.net/weixin_33871366/article/details/91377406)

+ 下述的 MaterialPageRoute 方式没有动画效果

```
Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => SecondRoute()),
  );

```

+ 如果想要一个像 iOS 上那样的滑动页面切换，可以用 CupertinoPageRoute

```
Navigator.push(
    context, CupertinoPageRoute(builder: (context) => Screen2()))
```

## flutter Swiper

+ 参考

> [flutter_swiper](https://github.com/best-flutter/flutter_swiper/blob/master/README-ZH.md)

## flutter 导航返回拦截WillPopScope(防误触)

+ [flutter 导航返回拦截WillPopScope(防误触)](https://www.jianshu.com/p/858ea277675f)

## flare_flutter

+ 参考

> [Flutter动画之Flare的制作与使用](https://www.jianshu.com/p/d5643ff3cf5f)
> 
> [Flutter使用Flare做动画](https://www.jianshu.com/p/a62fa1866a5f)

## Flutter 动画

+ 参考

> [Flutter 中的 Animations（一）](https://www.jianshu.com/p/3f2ae714f804)
> 
> [Flutter 中的 Animations（二）](https://www.jianshu.com/p/322e85c7fb6f)

### 必要的概念和类

+ Animation 对象，是 Flutter 动画库中的核心类，插入用于引导动画的值
+ Animation 对象知道当前动画的状态（如：动画是否开始，停止，前进或者后退），但对屏幕上显示的内容一无所知
+ AnimationController 对象管理着 Animation
+ CurvedAnimation 将动画定义成非线性运动的动画
+ Tween 在被动画对象使用的数据范围之间进行插值。例如，Tween 可能会定义从红色到蓝色或从 0 到 255 的插值
+ 使用 Listeners 和 StatusListeners 来监听动画状态的变化

### 步骤

+ 初始化一个 AnimationController 对象

```
AnimationController controller = AnimationController(duration: const Duration(milliseconds: 500), vsync: this);
```

+ 初始化一个 Animation 对象， 并将 AnimationController 作为参数传递进去。这里的 Animation 对象是通过 Tween 对象的 animate 方法创建的

```
Animation<int> alpha = IntTween(begin: 0, end:255).animate(controller);
```

+ 调用 AnimationController 的 forward() 方法执行动画

```
controller.forward();
```

+ 在 Widget 的 dispose() 方法中调用释放资源

```
controller.dispose();
```

### 案例

下面的案例是在给定的时间内改变 widget 的宽高

+ 我们需要实时获取 Animation 的 value 来赋给 widget 的宽高
+ 要改变 widget 的宽高，那么就需要 setState(...) 来让 widget 重绘

首先我们需要一个可以改变状态的 widget，也就是继承自 StatefulWidget ，然后按照我们上述的步骤来，代码如下：

```
class AnimateApp extends StatefulWidget {

  @override
  State<StatefulWidget> createState() {
    return _AnimateAppState();
  }
}

class _AnimateAppState extends State<AnimateApp> with SingleTickerProviderStateMixin {

  AnimationController controller;
  Animation<double> animation;
  
  @override
  void initState() {
    super.initState();
    // 创建 AnimationController 对象
    controller = AnimationController(
        vsync: this, duration: const Duration(milliseconds: 2000));
    // 通过 Tween 对象 创建 Animation 对象
    animation = Tween(begin: 50.0, end: 200.0).animate(controller)
      ..addListener(() {
        // 注意：这句不能少，否则 widget 不会重绘，也就看不到动画效果
        setState(() {});
      })
    // 执行动画
    controller.forward();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'AnimateApp',
        theme: ThemeData(
            primaryColor: Colors.redAccent
        ),
        home: Scaffold(
            appBar: AppBar(
              title: Text('AnimateApp'),
            ),
            body: Center(
              child: Container(
                // 获取动画的值赋给 widget 的宽高
                width: animation.value,
                height: animation.value,
                decoration: BoxDecoration(
                    color: Colors.redAccent
                ),
              ),
            )
        )
    );
  }

  @override
  void dispose() {
    // 资源释放
    controller.dispose();
    super.dispose();
  }
}
```

可以看出上面的动画是线性运动的，我们可以通过 CurvedAnimation 来实现非线性运动的动画代码如下：

```
controller = AnimationController(
    vsync: this, duration: const Duration(milliseconds: 2000));
// 非线性动画
final CurvedAnimation curve = CurvedAnimation(
    parent: controller, curve: Curves.elasticOut);
animation = Tween(begin: 50.0, end: 200.0).animate(curve)
  ..addListener(() {
    setState(() {});
  });
```

然后我们还可以给动画添加状态监听，通过给 Animation 添加 addStatusListener(...) 来监听当前动画的状态，如：动画是否播放完成。我们可以给上面的例子加一个状态监听，让动画无限执行：

```
animation = Tween(begin: 50.0, end: 200.0).animate(curve)
      ..addListener(() {
        setState(() {});
      })
      ..addStatusListener((status) {
        if (status == AnimationStatus.completed) {
          controller.reverse();
        } else if (status == AnimationStatus.dismissed) {
          controller.forward();
        }
      });
```

AnimationStatus.completed 表示动画在结束时停止的状态，这个时候我们让动画反向执行（从后往前）；AnimationStatus.dismissed 表示动画在开始时就停止的状态，这个时候我们让动画正常执行（从前往后）。这样就可以让动画无限执行了

Tween 还可以接受 Color 类型的参数，实现颜色渐变的效果，下面让 widget 的颜色从 红色 渐变到 蓝色，部分代码如下：

```
controller = AnimationController(
        duration: const Duration(milliseconds: 3000), vsync: this);
    animation = ColorTween(begin: Colors.redAccent, end: Colors.blue).animate(
        controller)
      ..addListener(() {
        setState(() {});
      });
    controller.forward();
    
...

child: Container(
        decoration: BoxDecoration(
            color: animation.value
        ),
        margin: EdgeInsets.symmetric(vertical: 10.0),
        height: 200.0,
        width: 200.0,
      ),
```

### AnimatedWidget

使用 AnimatedWidget 来实现动画，就不需要给动画 addListener(...) 和 setState((){}) 了，AnimatedWidget 自己会使用当前 Animation 的 value 来绘制自己。当然，这里 Animation 我们是以构造参数的方式传递进去的

```
class AnimatedContainer extends AnimatedWidget {

  AnimatedContainer({Key key, Animation<double> animation})
      : super (key: key, listenable: animation);

  @override
  Widget build(BuildContext context) {
    final Animation<double> animation = listenable;
    return Center(
      child: Container(
        decoration: BoxDecoration(
            color: Colors.redAccent
        ),
        margin: EdgeInsets.symmetric(vertical: 10.0),
        height: animation.value,
        width: animation.value,
      ),
    );
  }
}
```

上述代码中，我们定义了一个 AnimatedContainer 继承了 AnimatedWidget，然后定义了一个构造方法，注意，构造方法中我们定义了一个 Animation 然后把这个 Animation 传到父类（super）中去了，我们可以看看 listenable: animation 这个参数，是一个 Listenable 类型，如下：

```
/// The [Listenable] to which this widget is listening.
///
/// Commonly an [Animation] or a [ChangeNotifier].
final Listenable listenable;
```

然后再看看 Animation 类：

```
abstract class Animation<T> extends Listenable implements ValueListenable<T> {
...
}
```

可以看到 Animation 是 Listenable 的子类，所以在我们自定义的 AnimatedContainer 类中可以传一个 Animation 类型的的参数作为父类中 listenable 的值

使用我们上面定义的 AnimatedContainer 也很简单，直接作为 widget 使用就好，部分代码如下：

```
@override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'AnimatedWidgetDemo',
      theme: ThemeData(
          primaryColor: Colors.redAccent
      ),
      home: Scaffold(
          appBar: AppBar(
            title: Text('AnimatedWidgetDemo'),
          ),
          body: AnimatedContainer(animation: animation,)
      ),
    );``
  }
```

可以看出我们在实例化 AnimatedContainer 的时候传入了一个 Animation 对象

### AnimatedBuilder

我们先看看如何使用 AnimatedBuilder 做一个上面一样的效果

部分代码如下：

```
@override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'AnimatedBuilderExample',
      theme: ThemeData(primaryColor: Colors.redAccent),
      home: Scaffold(
        appBar: AppBar(
          title: Text('animatedBuilderExample'),
        ),
        body: Center(
          child: AnimatedBuilder(
            animation: _animation,
            child: Container(
              decoration: BoxDecoration(color: Colors.redAccent),
            ),
            builder: (context, child) {
              return Container(
                width: _animation.value,
                height: _animation.value,
                child: child,
              );
            },
          ),
        ),
      ),
    );
  }
```

因为 AnimatedBuilder 是继承于 AnimatedWidget 的，所以可以直接把 AnimatedBuilder 当作 widget 使用

```
class AnimatedBuilder extends AnimatedWidget { ... }
```

上述代码关键部分如下：

```
body: Center(
  child: AnimatedBuilder(
    animation: _animation,
    child: Container(
      decoration: BoxDecoration(color: Colors.redAccent),
    ),
    builder: (context, child) {
      return Container(
        width: _animation.value,
        height: _animation.value,
        child: child,
      );
    },
  ),
),
```

> builder 这个匿名类是每次动画值改变的时候就会被调用

AnimatedBuilder 使用简化后的结构如下：

```
AnimatedBuilder(
    animateion: ... ,
    child: ... ,
    builder: (context, child) {
        return Container(
            width: ... ,
            height: ... ,
            child: child
        )
    }
)
```

上述代码看着可能会有迷糊的地方，里面的 child 好像被指定了两次，外面一个，里面一个。其实，外面的 child 是传给 AnimatedBuilder 的，而 AnimatedBuilder 又将这个 child 作为参数传递给了里面的匿名类（builder）

我们可以验证上述说明，就是给外面的 child 指定一个 key，然后在 builder 里面打印出参数 child 的 key

```
body: Center(
  child: AnimatedBuilder(
    animation: _animation,
    child: Container(
      decoration: BoxDecoration(color: Colors.redAccent),
    key: Key("android"),
    ),
    builder: (context, child) {
      print("child.key: ${child.key}");
      return Container(
        width: _animation.value,
        height: _animation.value,
        child: child,
      );
    },
  ),
),
```

我们在外面的 child 里面的添加了一个 key 值，然后在 builder 里面打印出参数 child 的 key 值

输出如下：

```
flutter: child.key: [<'android'>]
```

### AnimatedSwitcher

+ 参考

> [通用“动画切换”组件（AnimatedSwitcher）](https://book.flutterchina.club/chapter9/animated_switcher.html)

### Flutter API 自带的动画组件

#### AnimatedAlign

+ 参考

> [Flutter之AnimatedAlign组件](https://blog.csdn.net/gzx110304/article/details/104567619/)

+ AnimatedAlign 可以通过改变子组件件的对齐方式,来控制其子组件的平移动画效果

```
AnimatedAlign({
  Key key,
  @required this.alignment,
  this.child,
  Curve curve = Curves.linear,
  @required Duration duration,
  VoidCallback onEnd,
})
```

+ 参数 : alignment

> alignment 的取值是一个实现了 AlignmentGeometry 的对象,如 Alignment 和 AlignmentDirectional
> 
> 在 Alignment 中是通过 x 和 y 两个成员变量的取值来表示子组件的对齐方式的
> 
> x 和 y 的值从 -1.0 到 1.0 之间取值,并分别表示水平方向和垂直方向的对其方式
> 
> 当 x = -1.0 时,表示子组件以父组件的左边缘对齐
> 
> 当 x = 0.0 时,表示子组件在水平方向上相对于父组件居中对齐
> 
> 当 x = 1.0 时,表示子组件以父组件的右边缘对齐
> 
> 当 y = -1.0 时,表示子组件以父组件的上边缘对齐
> 
>  当 y = 0.0 时,表示子组件在垂直方向上相对于父组件居中对齐
> 
> 当 y = 1.0 时,表示子组件以父组件的下边缘对齐
> 
> Alignment 的 9 个常量值与 x,y 取值的对应关系

```
static const Alignment topLeft = Alignment(-1.0, -1.0);
static const Alignment topCenter = Alignment(0.0, -1.0);
static const Alignment topRight = Alignment(1.0, -1.0);
static const Alignment centerLeft = Alignment(-1.0, 0.0);
static const Alignment center = Alignment(0.0, 0.0);
static const Alignment centerRight = Alignment(1.0, 0.0);
static const Alignment bottomLeft = Alignment(-1.0, 1.0);
static const Alignment bottomCenter = Alignment(0.0, 1.0);
static const Alignment bottomRight = Alignment(1.0, 1.0);
```

> 在 AlignmentDirectional 中是通过 start 和 y 两个成员变量的取值来表示子组件的对齐方式的
> 
> start 和 y 的值从 -1.0 到 1.0 之间取值,并分别表示水平方向和垂直方向的对齐方式
> 
> 其中在水平方向的对齐方式是由 start 的值和 TextDirection 的值来共同决定的, TextDirection 主要是确定开始位置和结束位置,例如 TextDirection.ltr 表示从左到右; TextDirection.rtl 表示从右到左; start 决定以父组件的哪里对齐
> 
> 在垂直方向上的对齐方式和 Alignment 类似
> 
> AlignmentDirectional 的 9 个常量值与 start, y 取值的对应关系

```
static const AlignmentDirectional topStart = AlignmentDirectional(-1.0, -1.0);
static const AlignmentDirectional topCenter = AlignmentDirectional(0.0, -1.0);
static const AlignmentDirectional topEnd = AlignmentDirectional(1.0, -1.0);
static const AlignmentDirectional centerStart = AlignmentDirectional(-1.0, 0.0);
static const AlignmentDirectional center = AlignmentDirectional(0.0, 0.0);
static const AlignmentDirectional centerEnd = AlignmentDirectional(1.0, 0.0);
static const AlignmentDirectional bottomStart = AlignmentDirectional(-1.0, 1.0);
static const AlignmentDirectional bottomCenter = AlignmentDirectional(0.0, 1.0);
static const AlignmentDirectional bottomEnd = AlignmentDirectional(1.0, 1.0);
```

+ 参数 : curve

> 控制动画执行的曲线

+ 参数 : duration

> 动画执行的时长,为一个 Duration 对象

```
Duration(milliseconds: 3000);
```

+ 参数 : child

> AnimateAlign 的子组件,动画的作用对象

#### AnimatedContainer


#### AnimatedCrossFade


#### Hero


#### AnimatedBuilder


#### DecoratedBoxTransition


#### FadeTransition


#### PositionedTransition/RelativePositionedTransition


#### RotationTransition


#### ScaleTransition


#### AlignTransition


#### SizeTransition


#### SlideTransition


#### AnimatedDefaultTextStyle


#### AnimatedListState


#### AnimatedModalBarrier


#### AnimatedOpacity


#### AnimatedPhysicalModel


#### AnimatedPositioned


#### AnimatedSize


#### AnimatedWidget


#### AnimatedWidgetBaseState


## Flutter 基础 Widgets

### Container

+ 参考

> [Flutter Container](https://www.jianshu.com/p/f4ca9a937034)

+ Container 构成以及绘制过程

> Container 作为 Flutter 中的用来布局的 Widget，可以对子 widget 进行绘制(painting)、定位(positioning)、调整大小(sizing)等操作

+ Container 的构成

> 从内至外：子widget -> padding -> constraints -> margin

+ 调整大小(sizing)

```
Container({
    Key key,
    this.alignment,
    this.padding,
    Color color,
    Decoration decoration,
    this.foregroundDecoration,
    double width,
    double height,
    BoxConstraints constraints,
    this.margin,
    this.transform,
    this.child,
  })
```

> 没有子节点的 Container 试图尽可能大，除非传入的约束(constraints)是无限制(unbounded)的，在这种情况下，它们尽可能地小
> 
> 拥有子节点的 Container，大小会按照子节点的大小进行适应。如果 Container 设置了大小参数（例如：width, height, constraints），则按照 Container 的大小参数来

+ 布局行为

> 由于 Container 包含了一系列其他的 Widget，所以 Container 的布局行为是由一系列其他的 Widget 的布局行为组合而成
> 
> *布局顺序*
> 
> Container 会按照下面的这个顺序去进行布局操作：
> 
> 对齐（alignment）
> 
> 调节自身大小去适应子节点
> 
> 优先使用 width 、 height、constraints
> 
> 放大自己去填充父节点
> 
> 尽可能的变小

+ 属性

> *Alignment - 约束 child 的位置*

```
class FlutterContainer extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
        child: Container(
          width: 300,
          height: 200,
          alignment: Alignment.centerRight,
          color: Colors.blue,
          child: Text("Hello"),
        )
    );
  }
}
```

> *Constraints - 控件占用的空间大小*
> 
> 一般使用 BoxConstraints

```
Center(
      child: Container(
        color: Colors.blue,
        alignment: Alignment.center,
        child: Container(
          color: Colors.brown,
          constraints: BoxConstraints(
              maxHeight: 300.0,
              maxWidth: 200.0,
              minWidth: 150.0,
              minHeight: 150.0
          ),
        ),
      ),
    );
```

> 没有子 child，给定了constraint，所以按照maxW、maxH来布局
> 
> 如果有子 child，给定了constraint，所以按照minW、minH来布局???

```
Center(
      child: Container(
        color: Colors.blue,
        alignment: Alignment.center,
        child: Container(
          color: Colors.brown,
          child: Text("hello"),
          constraints: BoxConstraints(
              maxHeight: 300.0,
              maxWidth: 200.0,
              minWidth: 150.0,
              minHeight: 150.0
          ),
        ),
      ),
    );
```

> *Margin - 给 Container 设置外边距*
> 
> 一般使用 EdgeInsets
> 
> 先看下默认情况：

```
Center(
      child: Container(
        color: Colors.blue,
        alignment: Alignment.centerRight,
        child: Container(
          color: Colors.brown,
          child: Text("HELLO"),
          constraints: BoxConstraints(
              maxHeight: 300.0,
              maxWidth: 200.0,
              minWidth: 150.0,
              minHeight: 150.0
          ),
        ),
      ),
    )
```

> 这里设置了 Alignment.centerRight，所以控件靠右居中。现在加上 EdgeInsets，看看

```
 Center(
      child: Container(
        color: Colors.blue,
        alignment: Alignment.centerRight,
        child: Container(
          margin: EdgeInsets.all(20.6),
          color: Colors.brown,
          child: Text("HELLO"),
          constraints: BoxConstraints(
              maxHeight: 300.0,
              maxWidth: 200.0,
              minWidth: 150.0,
              minHeight: 150.0
          ),
        ),
      ),
    );
```

> 可以看到 Container 距离右边有了一定的边距。需要注意的是 EdgeInsets.all 是距离四周的边距
> 
> 设置边距的其他方法：
> 
> fromLTRB (设置左上右下边距)
> 
> symmetric({ double vertical = 0.0, double horizontal = 0.0 })  设置垂直、水平的外边距

```
only({
this.left = 0.0,
this.top = 0.0,
this.right = 0.0,
this.bottom = 0.0
})
```

> *Padding - 设置 Container 内边距*
> 
> 与 Margin 类似，使用相同的方法

```
 Center(
      child: Container(
        constraints: BoxConstraints(
            minHeight: 100, minWidth: 200, maxWidth: 400, maxHeight: 200),
        child: Container(
          margin: EdgeInsets.all(20.5),
          padding: EdgeInsets.fromLTRB(30.4, 0, 0, 80),
        //设置padding内边距后，child居中偏移了位置
          color: Colors.brown,
          child: Text("HELLO"),
          alignment: Alignment.center,//child居中
        ),
      ),
    );
```

### Stack(层叠控件)

+ 参考 

> [Flutter 基础组件之 Stack](https://blog.csdn.net/zgcqflqinhao/article/details/85328665)
> 
> [Flutter 布局（八）- Stack、IndexedStack、GridView详解](https://www.jianshu.com/p/71adcf6431ec)

+ 如果说 Row 和 Column 相当于 Android 的 LinearLayout 的话，那么 Stack 就有点像 Android 中 FrameLayout，它可以使子组件堆叠起来，但是它比 FrameLayout 要强大，它可以控制子组件的位置，使用起来也是很简单的

+ 布局行为

> Stack 的布局行为，根据 child 是 positioned 还是 non-positioned 来区分
> 
> 对于 positioned 的子节点，它们的位置会根据所设置的 top、bottom、right 以及 left 属性来确定，这几个值都是相对于 Stack 的左上角
> 
> 对于 non-positioned 的子节点，它们会根据 Stack 的 aligment 来设置位置
> 
> 对于绘制 child 的顺序，则是第一个 child 被绘制在最底端，后面的依次在前一个 child 的上面，类似于 web 中的 z-index。如果想调整显示的顺序，则可以通过摆放 child 的顺序来进行

+ 构造方法

```
Stack({
  Key key,
  this.alignment = AlignmentDirectional.topStart,
  this.textDirection,
  this.fit = StackFit.loose,
  this.overflow = Overflow.clip,
  List<Widget> children = const <Widget>[],
})
```

> Stack 只有这一个构造方法，而且也没有必须指定的属性，但是一般都会设置 children 属性，不然也没有什么意义

+ 常用属性

> *alignment*
> 
> 子组件对齐方式，同 Container 的 alignment 属性一样的，它指定的是所有子组件的对齐方式，所以建议在只有两个子组件的时候使用，如果有三个及以上的子组件时，建议使用 Positioned 包裹子组件来决定子组件的位置
> 
> alignment 的可选值有：
> 
> AlignmentDirectional.topCenter：子组件垂直靠顶部水平居中对齐
> 
> AlignmentDirectional.topRight：子组件垂直靠顶部水平靠右对齐
> 
> AlignmentDirectional.centerLeft：子组件垂直居中水平靠左对齐
> 
> AlignmentDirectional.center：子组件垂直和水平居中都对齐
> 
> AlignmentDirectional.centerRight：子组件垂直居中水平靠右对齐
> 
> AlignmentDirectional.bottomLeft：子组件垂直靠底部水平靠左对齐
> 
> AlignmentDirectional.bottomCenter：子组件垂直靠底部水平居中对齐
> 
> AlignmentDirectional.bottomRight：子组件垂直靠底部水平靠右对齐
> 
> 也可以使用 alignmentDirectional(start,y) 指定具体的偏移量，start 就相当于 x，它是以整个组件的中心为坐标原点，x、y 偏移量取值范围为 [-1,1]，如果 x 的偏移量大于 0，则表示向右偏移，小于 0 则向左偏移；如果 y 轴的偏移量大于 0 则向下偏移，小于 0 则向上偏移
> 
> *textDirection*
> 
> 子组件排列方向，可选值有：
> 
> TextDirection.ltr：从左往右排列
> 
> TextDirection.rtl：从右往左排列
> 
> *fit*
> 
> 如何确定没有使用 Position 包裹的子组件的大小，可选值有：
> 
> StackFit.loose：子组件宽松取值，可以从 min 到 max
> 
> StackFit.expand：子组件取最大值
> 
> StackFit.passthrough：不改变子组件约束条件
> 
> *overflow*
> 
> 超出部分的处理方式，可选值有 Overflow.clip 和 Overflow.visible，不过我没有看到该属性的效果

+ Demo

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      //是否显示 debug 标签
      debugShowCheckedModeBanner: false,
      title: "Stack",
      home: Scaffold(
        appBar: AppBar(
          title: Text("Stack"),
        ),
        body: Container(
          child: Stack(
            //子组件对齐方式，同 Container 的 alignment 属性一样的，它指定的是所有子组件的对齐方式，所以建议在只有两个子组件的时候
            //使用，如果有三个及以上的子组件时，建议使用 Positioned 包裹子组件来决定子组件的位置，alignment 的可选值有：
            //AlignmentDirectional.topCenter：垂直靠顶部水平居中对齐
            //AlignmentDirectional.topRight：垂直靠顶部水平靠右对齐
            //AlignmentDirectional.centerLeft：垂直居中水平靠左对齐
            //AlignmentDirectional.center：垂直和水平居中都对齐
            //AlignmentDirectional.centerRight：垂直居中水平靠右对齐
            //AlignmentDirectional.bottomLeft：垂直靠底部水平靠左对齐
            //AlignmentDirectional.bottomCenter：垂直靠底部水平居中对齐
            //AlignmentDirectional.bottomRight：垂直靠底部水平靠右对齐
            //也可以像我一样指定具体的偏移量，它是以整个组件的中心为坐标原点，x、y 偏移量取值范围为 [-1,1]，如果 x 的偏移量大于 0
            //则表示向右偏移，小于 0 则向左偏移；如果 y 轴的偏移量大于 0 则向下偏移，小于 0 则向上偏移。
            alignment: AlignmentDirectional(0.8, -0.8),
            //子组件排列方向，可选值有：
            //TextDirection.ltr：从左往右排列
            //TextDirection.rtl：从右往左排列
            textDirection: TextDirection.ltr,
            //如何确定没有使用 Position 包裹的子组件的大小，可选值有：
            //StackFit.loose：子组件宽松取值，可以从 min 到 max
            //StackFit.expand：子组件取最大值
            //StackFit.passthrough：不改变子组件约束条件
            fit: StackFit.loose,
            //超出部分的处理方式，可选值有 Overflow.clip 和 Overflow.visible，不过我没有看到该属性的效果
//            overflow: Overflow.clip,
            children: <Widget>[
              CircleAvatar(
                backgroundImage: AssetImage("assets/images/a.jpg"),
                radius: 100,
              ),
              Text(
                "Itachi",
                style: TextStyle(fontSize: 30, color: Color(0xFF000000)),
              ),
              Positioned(
                //距离左边的距离
                left: 10,
                //距离顶部的距离
//                top: 10,
                //距离右边的距离，设置 left 后该距离失效
//                right: 10,
                //距离底部的距离，设置 top 后该距离失效
                bottom: 10,
//                //子组件的宽、高，注意，宽高与 top、left、bottom、right
//                width: 100,
//                height: 100,
                child: Text(
                  "鼬",
                  style: TextStyle(fontSize: 40, color: Color(0xFF000000)),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

+ Positioned

> 用来在 Stack 组件中辅助子组件定位的组件，建议在有三个及以上子组件的复杂布局时使用，它的常用属性有如下 6  个：
> 
> left：距离左边的距离
> 
> top：距离顶部的距离
> 
> right：距离右边的距离，设置 left 后该距离失效
> 
> bottom：距离底部的距离，设置 top 后该距离失效
> 
> width 和 height：子组件的宽
> 
> height：子组件的高
> 
> 注意，width、left、right 不能同时设置，height、top、bottom 也不能同时设置

### Align

> 参考 : [Flutter 基础布局Widgets之Align详解](https://www.jianshu.com/p/8782d7eea799)

+ 一般来说，Align的使用都是作为其他控件的一个参数，目的是为了设置子 child 的对齐方式，比如居中，左上，右下等多个对齐方向，其本身用法也多灵活

+ 构造函数

```
const Align({
    Key key,
    this.alignment = Alignment.center,
    this.widthFactor,
    this.heightFactor,
    Widget child
  })
```

> * alignment 设置对齐方向，有多种设置方式：*
> 
> 比如：`FractionalOffset(0.5, 0.5) == Alignment(0.0,0.0) == Alignment.center` ，都是将子 child 居中对齐的控制方式
> 
> Alignment(0.0,0.0) 表示矩形的中心。从 -1.0 到 +1.0 的距离是矩形的一边到另一边的距离
> 
> 而 Alignment 中还可以这样使用对齐方式的控制，也是较为常用的使用方式：

```
/// The top left corner.
  static const Alignment topLeft = Alignment(-1.0, -1.0);

  /// The center point along the top edge.
  static const Alignment topCenter = Alignment(0.0, -1.0);

  /// The top right corner.
  static const Alignment topRight = Alignment(1.0, -1.0);

  /// The center point along the left edge.
  static const Alignment centerLeft = Alignment(-1.0, 0.0);

  /// The center point, both horizontally and vertically.
  static const Alignment center = Alignment(0.0, 0.0);

  /// The center point along the right edge.
  static const Alignment centerRight = Alignment(1.0, 0.0);

  /// The bottom left corner.
  static const Alignment bottomLeft = Alignment(-1.0, 1.0);

  /// The center point along the bottom edge.
  static const Alignment bottomCenter = Alignment(0.0, 1.0);

  /// The bottom right corner.
  static const Alignment bottomRight = Alignment(1.0, 1.0);
```

> 即本质就是类似于语法糖将各个方向的对齐方式简单封装了下
> 
> FractionalOffset() 类似 Alignment() ，但是坐标起点是左上角，且范围为 0~1。比如：FractionalOffset(0.5, 0.5) 代表中间位置
> 
> *widthFactor*
> 
> 如果非空，则将其宽度设置为子元素的宽度乘以该因子，可以大于或小于1.0，但必须是正数
> 
> *heightFactor*
> 
> 如果非空，则将其高度设置为子元素的高度乘以该因子，可以大于或小于1.0，但必须是正数

+ 示例代码

```
// align

import 'package:flutter/material.dart';

class AlignLearn extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: AppBar(
        title: Text('Align')
      ),
      // 对齐小部件
      body: Align(
          // Alignment(0.0,0.0)表示矩形的中心。从-1.0到+1.0的距离是矩形的一边到另一边的距离。
          // alignment: Alignment(1, 0),
          // FractionalOffset(1, 1) 类似Alignment() 但是坐标起点是左上角，且范围为0~1 比如 FractionalOffset(0.5, 0.5) 代表中间位置
          alignment: Alignment.bottomRight,
          child: Container(
            color: Colors.blueAccent,
            width: 100,
            height: 100,
          ),
      ),
    );
  }
}
```

### SafeArea

> 参考 : [Flutter SafeArea](https://www.jianshu.com/p/c6320f61a9b7)

+ 先看代码

```
class FlutterAlign extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Align(
      alignment: Alignment(-1, -1),
      child: Container(
        child: Text(
          "Hello",
        ),
      ),
    );
  }
}
```

> 可以看到，在刘海屏幕中，显示位置不是我们期待的。大部分刘海区域不是我们所触发按钮的区域
> 
> 可以使用 SafeArea Widget 来很好的解决这个问题

```
class FlutterAlign extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Align(
        alignment: Alignment(-1, -1),
        child: Container(
          child: Text(
            "Hello",
          ),
        ),
      ),
    );
  }
}
```

> 使用这个 Widget 也能很好的处理 iPhone X 类似的底部 bottom 的区域

```
class FlutterAlign extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Align(
        alignment: Alignment(-1, 1),
        child: Container(
          child: Text(
            "Hello",
          ),
        ),
      ),
    );
  }
}
```

### InkWell

+ 参考

> [Flutter InkWell-水波纹效果](https://www.jianshu.com/p/93e32915bb9e)

+ InkWell 有的叫溅墨效果，有的叫水波纹效果。使用场景是给一些无点击事件的部件添加点击事件时使用（也支持长按、双击等事件），同时你也可以去修改它的颜色和形状

```
InkWell(
  borderRadius: BorderRadius.circular(8.0), // 圆角
  splashColor: Colors.transparent, // 溅墨色（波纹色）
  highlightColor: Colors.transparent, // 点击时的背景色（高亮色）
  onTap: () {},// 点击事件
  child: Container(),
);
```

+ 实现水波纹效果 两种方式

> *包一层 Material，将背景色设置在 Material中的 color 里*

```
Material(
  color: Colors.white,
  child: InkWell(),
)
```

> *使用 Stack 布局，将 InkWell 放置在上层。这种适用于给图片添加点击效果，比如 Banner 图的点击*

```
Stack(
    children: <Widget>[
      Positioned.fill(
        child: Image(),
      ),
      Positioned.fill(
        child: Material(
          color: Colors.transparent,
          child: InkWell(
            splashColor: Color(0X40FFFFFF),
            highlightColor: Colors.transparent,
            onTap: () {},
          ),
        ),
      )
    ],
  )
```

### CustomScrollView

+ 参考资料

> [Flutter 实战 - CustomScrollView](https://book.flutterchina.club/chapter6/custom_scrollview.html)

+ CustomScrollView是可以使用Sliver来自定义滚动模型（效果）的组件

> 它可以包含多种滚动模型，举个例子，假设有一个页面，顶部需要一个GridView，底部需要一个ListView，而要求整个页面的滑动效果是统一的，即它们看起来是一个整体。如果使用GridView+ListView来实现的话，就不能保证一致的滑动效果，因为它们的滚动效果是分离的，所以这时就需要一个"胶水"，把这些彼此独立的可滚动组件"粘"起来，而CustomScrollView的功能就相当于“胶水”
> 
> 在Flutter中，Sliver通常指可滚动组件子元素（就像一个个薄片一样）。但是在CustomScrollView中，需要粘起来的可滚动组件就是CustomScrollView的Sliver了，如果直接将ListView、GridView作为CustomScrollView是不行的，因为它们本身是可滚动组件而并不是Sliver！因此，为了能让可滚动组件能和CustomScrollView配合使用，Flutter提供了一些可滚动组件的Sliver版，如SliverList、SliverGrid等。实际上Sliver版的可滚动组件和非Sliver版的可滚动组件最大的区别就是前者不包含滚动模型（自身不能再滚动），而后者包含滚动模型 ，也正因如此，CustomScrollView才可以将多个Sliver"粘"在一起，这些Sliver共用CustomScrollView的Scrollable，所以最终才实现了统一的滑动效果

### Row & Column

+ 参考资料

> [Flutter学习之MainAxisAlignment属性详解](https://www.jianshu.com/p/d9b5fd16c098)

+ MainAxisAlignment 属性

> MainAxisAlignment 属性就是代表主轴方向的对齐方式
> 
> MainAxisAlignment 里面一共有6个值，分别是 start，center，end，spaceBetween，spaceAround，spaceEvenly
> 
> `MainAxisAlignment.spaceBetween` : Place the free space evenly between the children
> 
> `MainAxisAlignment.spaceAround` : Place the free space evenly between the children as well as half of that space before and after the first and last child
> 
> `MainAxisAlignment.spaceEvenly` : Place the free space evenly between the children as well as before and after the first and last child

### BoxDecoration

+ 参考资料

> [Flutter之BoxDecoration用法详解](https://www.jianshu.com/p/9012bc9e2feb)
> 
> *非常详细，值得参考*


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

