# Dart
+ [A tour of the Dart language](https://dart.dev/guides/language/language-tour)

## Dart SDK安装
- brew tap dart-lang/dart
- brew install dart
- brew info dart

## [mac 上配置flutter开发环境](https://www.jianshu.com/p/eb782589be82)

# 安装flutter SDK
+ 步骤一: [下载](https://flutter.dev/docs/get-started/install/macos)
+ 步骤二: cd ~/Applications
+ 步骤三: unzip ~/Downloads/flutter_macos_v1.12.13+hotfix.5-stable.zip
+ 步骤四: 在~/.bash_profile中添加:

> FLUTTER_HOME=/Users/lvweiwei/Applications/flutter
> 
> export PATH=$PATH:$FLUTTER_HOME/bin
> 

+ 步骤五: source ~/.bash_profile

# 网上资源
+ [flutter 官网](https://flutter.dev)

# 填坑记录
## 在Idea中dart运行出现：Setting VM flags failed: Unrecognized flags: checked
- Run -> Edit Configurations...中去掉Checked Mode