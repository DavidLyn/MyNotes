---
# [Bootstrap into Dart](https://flutter.dev/docs/resources/bootstrap-into-dart)

+ 对 Dart 语言不熟悉？我们汇编了我们最喜欢的资源，帮助您快速学习 Dart。很多人都说 Dart 学起来既简单又有趣。我们希望这些资源也能让你更容易学习 Dart

+ [Language tour](https://dart.dev/guides/language/language-tour)

> 对 Dart 语言最好的介绍。了解 Dart 的特性，如强类型、闭包、库、词法范围、顶层函数、命名参数、异步/等待等等

+ [Library tour](https://dart.dev/guides/libraries/library-tour)

> 对 Dart 强大的核心库有一个很好的概述。了解Dart对集合、异步、数学、数字、字符串、JSON等的支持

+ [Intro to Dart for Java Developers codelab](https://codelabs.developers.google.com/codelabs/from-java-to-dart)

> 使用您的 Java 知识快速启动和运行 Dart 。通过 Java 教程中的示例了解类、构造函数、参数和接口

+ [Effective Dart](https://dart.dev/guides/language/effective-dart)

> 样式、创作文档、用法等指南

+ [Asynchronous programming: futures, async, await](https://dart.dev/codelabs/async-await)

> 学习如何使用futures、async 和 await 关键字编写异步代码

+ [Asynchronous programming: streams](https://dart.dev/tutorials/language/streams)

> 了解如何使用 stream 执行异步 I/O 和事件处理

---
# [Language tour](https://dart.dev/guides/language/language-tour)

## A basic Dart program

+ 以下代码使用了 Dart 的许多基本功能：

```
// Define a function.
printInteger(int aNumber) {
  print('The number is $aNumber.'); // Print to console.
}

// This is where the app starts executing.
main() {
  var number = 42; // Declare and initialize a variable.
  printInteger(number); // Call a function.
}
```

+ // This is a comment.

> 单行注释。Dart还支持多行和文档注释

+ int

> 一种类型。其他一些内置类型是 String、List 和 bool

+ 42

> 数字字面量。数字字面量是一种编译时常量

+ print()

> 显示输出的简便方法

+ '...' (or "...")

> 字符串字面量

+ $variableName (or ${expression})

> 字符串插值：在字符串字面量中包含变量或表达式的等效字符串

+ main()

> 启动应用程序执行的特殊、必需的顶级函数

+ var

> 一种声明变量而不指定其类型的方法

## 重要概念

+ 变量中的所有内容都是对象，每个对象都是类的实例。包括数字、函数和 null 都是对象。所有对象都继承自 Object 类

+ 尽管 Dart 是强类型的，但类型注释是可选的，因为 Dart 可以推断类型。在上面的代码中，数字被推断为 int 类型。当您想明确表示不需要类型时，请使用特殊类型 dynamic

+ Dart支持泛型，如List<int>（整数列表）或List<dynamic>（任何类型的对象列表）

+ Dart 支持顶级函数（例如 main（））以及绑定到类或对象的函数（分别是静态方法和实例方法）。也可以在函数（嵌套函数或局部函数）中创建函数

+ 类似地，Dart 支持顶级变量以及绑定到类或对象的变量（静态和实例变量）。实例变量有时称为字段或属性

+ 与 Java 不同，Dart 没有 public、protected 和 private 关键字。如果标识符以下划线（_）开头，则它是其库的私有项

+ 标识符可以以字母或下划线（_）开头，后跟这些字符和数字的任意组合

+ Dart 既有表达式（有运行时值），也有语句（没有运行时值）。比如，条件表达式 `condition ? expr1 : expr2` 有值 expr1 或者 expr2。作为对比，语句 if-else 则没有值。一条语句可能包含一个或多个表达式，而表达式则不能直接包含语句

+ Dart 工具可以报告两种问题：警告和错误。警告只是表示代码可能无法工作，但不会阻止程序执行。错误可以是编译时错误，也可以是运行时错误。编译时错误阻止代码执行；运行时错误导致在代码执行时引发异常

## 关键词

+ 下表列出了 Dart 语言特别处理的单词

> 略

+ 避免使用这些单词作为标识符。如果需要，标有上标的关键字可以作为标识符：

> 上标1的单词是上下文关键字，只有在特定的地方才有意义。它们在任何地方都是有效的标识符
> 
> 上标2的单词是内置的标识符。为了简化将 JavaScript 代码移植到 Dart，这些关键字在大多数地方都是有效的标识符，但不能用作类或类型名，也不能用作导入前缀
> 
> 上标为3的单词是与Dart 1.0版本之后添加的异步支持相关的较新的、有限的保留单词。在任何标记为async、async* 或sync的函数体中，都不能使用await或yield作为标识符

+ 表中所有其他单词都是保留字，不能是标识符

## 变量

+ 下面是创建并初始化变量的示例：

```
var name = 'Bob';
```

> 变量存储引用。名为 name 的变量包含对值为 “Bob” 的字符串对象的引用
> 
> name 变量的类型被推断为字符串，但可以通过指定该类型来更改该类型。如果对象不限制为单一类型，请指定 Object 或 dynamic 类型

```
dynamic name = 'Bob';
```

> 另一个选择是显式声明要推断的类型：

```
String name = 'Bob';
```

+ 默认值

> 未初始化的变量的初始值为空。即使是数值类型的变量最初也是 null，因为数值和 Dart 中的其他所有东西一样都是对象

```
int lineCount;
assert(lineCount == null);
```

> 注意：生产代码忽略 assert（）调用。另一方面，在开发过程中，如果条件为 false， assert（condition）将抛出异常

+ Final 和 const

> 如果您从未打算更改变量，请使用 final 或 const，而不是 var 或明确类型。final 变量只能设置一次；const 变量是编译时常量。const 变量是隐式的 final。一个 final 的 top-level 和类变量在第一次使用时初始化
> 
> 注意：实例变量可以是 final，但不能是 const。必须在构造函数体开始之前初始化 final 实例变量-在变量声明处、通过构造函数参数或在构造函数的初始值设定项列表中
> 
> 下面是创建和设置 final 变量的示例：

```
final name = 'Bob'; // Without a type annotation
final String nickname = 'Bobby';
```

> 不能更改 final 变量的值：

```
name = 'Alice'; // Error: a final variable can only be set once.
```

> 对于要成为编译时常量的变量，请使用 const。如果 const 变量在类级别，则将其标记为 static const。在声明变量时，请将该值设置为编译时常量，例如数字或字符串文本、常量变量或对常量执行算术运算的结果：

```
const bar = 1000000; // Unit of pressure (dynes/cm2)
const double atm = 1.01325 * bar; // Standard atmosphere
```

> const 关键字不仅仅用于声明常量变量。您还可以使用它来创建常量值，以及声明创建常量值的构造函数。任何变量都可以有一个常量

```
var foo = const [];
final bar = const [];
const baz = []; // Equivalent to `const []`
```

> 可以从 const 声明的初始化表达式中省略 const，就像上面的 baz 一样
> 
> 可以更改非 final、非 const 变量的值，即使它以前具有 const 值

```
foo = [1, 2, 3]; // Was const []
```

> 不能更改 const 变量的值：

```
baz = [42]; // Error: Constant variables can't be assigned a value.
```

> 从 Dart 2.5开始，可以在定义常量时使用类型检查和强制转换（is 和 As）、collection if 和 spread运算符（... 还有 ...？）

```
// Valid compile-time constants as of Dart 2.5.
const Object i = 3; // Where i is a const Object with an int value...
const list = [i as int]; // Use a typecast.
const map = {if (i is int) i: "int"}; // Use is and collection if.
const set = {if (list is List<int>) ...list}; // ...and a spread.
```

+ 内置类型

> Dart 语言特别支持以下类型：
> 
> numbers、strings、booleans、lists (also known as arrays)、sets、maps、runes (for expressing Unicode characters in a string)、symbols
> 
> 可以使用文本初始化这些特殊类型的对象。例如，“this is a string”是字符串文本，true 是布尔文本
> 
> 因为 Dart 中的每个变量都指向一个对象一个类的实例，所以通常可以使用构造函数初始化变量。一些内置类型有自己的构造函数。例如，可以使用 Map（）构造函数创建 map

+ Numbers

> Dart 有两种数据类型：
> 
> *int*
> 
> 整数值不大于64位，具体取决于平台。在 Dart 虚拟机上，值可以是  -263 到 263-1。编译成 JavaScript 的 Dart 使用 JavaScript 数字，允许 -253 到 253-1 之间的值
> 
> *double*
> 
> 由 IEEE 754 标准指定的64位（双精度）浮点数
> 
> int 和 double 都是 num 的子类型。num 类型包括基本的运算符，如+、-、/、和*，在其他方法中还可以找到 abs（）、ceil（）和 floor（）。按位运算符（如 >> ）在 int 类中定义。如果 num 及其子类型没有您要查找的内容，dart:math 库可能有
> 
> 整数是没有小数点的数字。下面是一些定义整型字面量的示例：

```
var x = 1;
var hex = 0xDEADBEEF;
```

> 如果一个数字包含小数，它就是一个 double。下面是一些定义双字面值的示例：

```
var y = 1.1;
var exponents = 1.42e5;
```

> 从 Dart 2.1 开始，整数字面量在必要时自动转换为 double：

```
double z = 1; // Equivalent to double z = 1.0.
```

> 版本说明：在 Dart 2.1 之前，在 double 上下文中使用整数字面量是错误的
> 
> 下面是如何将字符串转换为数字，或者反过来：

```
// String -> int
var one = int.parse('1');
assert(one == 1);

// String -> double
var onePointOne = double.parse('1.1');
assert(onePointOne == 1.1);

// int -> String
String oneAsString = 1.toString();
assert(oneAsString == '1');

// double -> String
String piAsString = 3.14159.toStringAsFixed(2);
assert(piAsString == '3.14');
```

> int 类型指定传统的按位移位（<<，>>）和（&）和或（|）运算符。例如：

```
assert((3 << 1) == 6); // 0011 << 1 == 0110
assert((3 >> 1) == 1); // 0011 >> 1 == 0001
assert((3 | 4) == 7); // 0011 | 0100 == 0111
```

> 文字数字是编译时常量。许多算术表达式也是编译时常量，只要它们的操作数是计算为数字的编译时常量

```
const msPerSecond = 1000;
const secondsUntilRetry = 5;
const msUntilRetry = secondsUntilRetry * msPerSecond;
```

+ Strings

> Dart 字符串是 UTF-16 代码单元的序列。可以使用单引号或双引号创建字符串：

```
var s1 = 'Single quotes work well for string literals.';
var s2 = "Double quotes work just as well.";
var s3 = 'It\'s easy to escape the string delimiter.';
var s4 = "It's even easier to use the other delimiter.";
```

> 可以使用 ${expression} 将表达式的值放入字符串中。如果表达式是标识符，则可以跳过{}。要获取与对象对应的字符串，Dart 调用对象的 toString（）方法

```
var s = 'string interpolation';

assert('Dart has $s, which is very handy.' ==
    'Dart has string interpolation, ' +
        'which is very handy.');
assert('That deserves all caps. ' +
        '${s.toUpperCase()} is very handy!' ==
    'That deserves all caps. ' +
        'STRING INTERPOLATION is very handy!');
```

> 注意：== 操作符测试两个对象是否等价。如果两个字符串包含相同的代码单元序列，则它们是等效的
> 
> 可以使用相邻字符串文本或+运算符连接字符串：

```
var s1 = 'String '
    'concatenation'
    " works even over line breaks.";
assert(s1 ==
    'String concatenation works even over '
        'line breaks.');

var s2 = 'The + operator ' + 'works, as well.';
assert(s2 == 'The + operator works, as well.');
```

> 创建多行字符串的另一种方法是：使用带有单引号或双引号的三引号：

```
var s1 = '''
You can create
multi-line strings like this one.
''';

var s2 = """This is also a
multi-line string.""";
```

> 可以通过在“原始”字符串前面加上 r 来创建该字符串：

```
var s = r'In a raw string, not even \n gets special treatment.';
```

> 只要任何插值表达式是计算为空或数值、字符串或布尔值的编译时常量，文字字符串就是编译时常量

```
// These work in a const string.
const aConstNum = 0;
const aConstBool = true;
const aConstString = 'a constant string';

// These do NOT work in a const string.
var aNum = 0;
var aBool = true;
var aString = 'a string';
const aConstList = [1, 2, 3];

const validConstString = '$aConstNum $aConstBool $aConstString';
// const invalidConstString = '$aNum $aBool $aString $aConstList';
```

+ Booleans

> 为了表示布尔值，Dart 有一个名为 bool 的类型。只有两个对象具有 bool 类型：boolean 文本 true 和 false，它们都是编译时常量
> 
> Dart 的类型安全性意味着不能使用if（nonbooleanValue）或assert（nonbooleanValue）这样的代码。相反，显式检查值，如下所示：

```
// Check for an empty string.
var fullName = '';
assert(fullName.isEmpty);

// Check for zero.
var hitPoints = 0;
assert(hitPoints <= 0);

// Check for null.
var unicorn;
assert(unicorn == null);

// Check for NaN.
var iMeantToDoThis = 0 / 0;
assert(iMeantToDoThis.isNaN);
```

+ Lists

> 在几乎每种编程语言中，最常见的集合可能是数组或对象的有序组。在 Dart 中，数组是 List 对象，所以大多数人都称它们为 List
> 
> Dart 列表字面量看起来像 JavaScript 数组字面量。下面是一个简单的 Dart 列表：

```
var list = [1, 2, 3];
```

> 注：Dart 推断列表的类型为 List <int>。如果尝试将非整数对象添加到此列表中，分析器或运行时将引发错误
> 
> List 使用基于零的索引，其中0是第一个元素的索引，list.length-1 是最后一个元素的索引。您可以获取列表的长度并引用列表元素，就像在 JavaScript 中一样：

```
var list = [1, 2, 3];
assert(list.length == 3);
assert(list[1] == 2);

list[1] = 1;
assert(list[1] == 1);
```

> 要创建编译时常量列表，请在列表文本之前添加 const：

```
var constantList = const [1, 2, 3];
// constantList[1] = 1; // Uncommenting this causes an error.
```

> Dart 2.3 引入了 spread 运算符（…）和 null-aware spread 运算符（…？），它提供了将多个元素插入到集合中的简明方法
> 
> 例如，可以使用 spread 运算符（…）将列表中的所有元素插入到另一个列表中：

```
var list = [1, 2, 3];
var list2 = [0, ...list];
assert(list2.length == 4);
```

> 如果 spread 运算符右侧的表达式可能为空，则可以使用 ull-aware spread 运算符（…？）来避免异常:

```
var list;
var list2 = [0, ...?list];
assert(list2.length == 1);
```

> Dart 2.3 还引入了 collection if 和 collection for，您可以使用它们使用条件（if）和重复（for）来构建集合
> 
> 下面是使用 collection if 创建包含三个或四个项的列表的示例：

```
var nav = [
  'Home',
  'Furniture',
  'Plants',
  if (promoActive) 'Outlet'
];
```

> 下面是使用 collection for 在将列表项添加到另一个列表之前操作列表项的示例：

```
var listOfInts = [1, 2, 3];
var listOfStrings = [
  '#0',
  for (var i in listOfInts) '#$i'
];
assert(listOfStrings[1] == '#1');
```

> 有关使用 collection if 和 For 的更多详细信息和示例，请参阅 [control flow collections proposal](https://github.com/dart-lang/language/blob/master/accepted/2.3/control-flow-collections/feature-specification.md)
> 
> 列表类型有许多处理列表的简便方法。有关列表的详细信息，请参见 [泛型](https://dart.dev/guides/language/language-tour#generics) 和 [集合](https://dart.dev/guides/libraries/library-tour#collections)

+ Sets

> 一个集合在 Dart 中是一个独特项目的无序集合。对集合的 Dart 支持由集合字面值和集合类型提供
> 
> 版本说明：虽然集合类型一直是 Dart 的核心部分，但是集合字面量在 Dart 2.2 中引入
> 
> 下面是一个简单的 Dart 集合，使用集合字面量创建：

```
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
```

> 注：Dart 推断 halogens 的类型为 Set <String>。如果试图向集合中添加错误类型的值，分析器或运行时将引发错误
> 
> 如果要创建空集，请在前面使用 {} 和类型参数，或将 {} 赋给类型集的变量：

```
var names = <String>{};
// Set<String> names = {}; // This works, too.
// var names = {}; // Creates a map, not a set.
```

> 集合还是 map？map 字面量语法与集合字面量的语法类似。因为 map 字面量优先，{}默认为 map 类型。如果忘记了 {} 上的类型注释或它被分配给的变量，那么 Dart 将创建 Map<dynamic，dynamic> 类型的对象
> 
> 使用 add（）或 addAll（）方法向现有集合添加项：

```
var elements = <String>{};
elements.add('fluorine');
elements.addAll(halogens);
```

> 使用 .length 获取集合中的项目数：

```
var elements = <String>{};
elements.add('fluorine');
elements.addAll(halogens);
assert(elements.length == 5);
```

> 要创建一个编译时常量集，请在 set 文本之前添加 const：

```
final constantSet = const {
  'fluorine',
  'chlorine',
  'bromine',
  'iodine',
  'astatine',
};
// constantSet.add('helium'); // Uncommenting this causes an error.
```

> 从 Dart 2.3 开始，集合支持 spread 运算符（... 和 ...?）集合 ifs 和 fors，就像列表一样

+ Maps

> 通常，Map 是关联键和值的对象。键和值都可以是任何类型的对象。每个键只出现一次，但可以多次使用相同的值。Map 的 Dart 支持由 Map 字面量和 Map 类型提供
> 
> 下面是一些使用 Map 字面量创建的简单 Dart Map：

```
var gifts = {
  // Key:    Value
  'first': 'partridge',
  'second': 'turtledoves',
  'fifth': 'golden rings'
};

var nobleGases = {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};
```

> 注：Dart 推断 gifts 的类型为 Map<String，String> ，Noblegas 的类型为 Map<int，String>。如果试图向 Map 添加错误类型的值，分析器或运行时将引发错误
> 
> 可以使用 Map 构造函数创建相同的对象：

```
var gifts = Map();
gifts['first'] = 'partridge';
gifts['second'] = 'turtledoves';
gifts['fifth'] = 'golden rings';

var nobleGases = Map();
nobleGases[2] = 'helium';
nobleGases[10] = 'neon';
nobleGases[18] = 'argon';
```

> 注意：您可能希望看到 new Map（）而不仅仅是 Map（）。从 Dart 2 开始，new 关键字是可选的
> 
> 向现有 Map 添加新的键值对，就像在 JavaScript 中一样：

```
var gifts = {'first': 'partridge'};
gifts['fourth'] = 'calling birds'; // Add a key-value pair
```

> 像在 JavaScript 中一样从 Map 中检索值：

```
var gifts = {'first': 'partridge'};
assert(gifts['first'] == 'partridge');
```

> 如果您查找的 key 不在 map 中，则返回空值：

```
var gifts = {'first': 'partridge'};
assert(gifts['fifth'] == null);
```

> 使用 .length 获取 map 中的键值对数：

```
var gifts = {'first': 'partridge'};
gifts['fourth'] = 'calling birds';
assert(gifts.length == 2);
```

> 要创建编译时常量的 map，请在 map 字面量之前添加 const：

```
final constantMap = const {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};

// constantMap[2] = 'Helium'; // Uncommenting this causes an error.
```

> 从 Dart 2.3 开始，maps 支持 spread 运算符（... 和 ...?）集合 if 和 for，就像列表一样

+ Runes and grapheme clusters

> 在 Dart 中，runes 公开字符串的 Unicode 代码点。从 Dart 2.6 开始，使用characters 包查看或操作用户感知(user-perceived)的字符
> 
> Unicode 为世界上所有书写系统中使用的每个字母、数字和符号定义唯一的数值。因为 Dart 字符串是 UTF-16 代码单元的序列，所以在字符串中表示 Unicode 代码点需要特殊的语法。表示 Unicode 码位的常用方法是 \uxxx，其中 XXXX 是一个4位十六进制值。例如，心形字符(♥) 是 \u2665。若要指定多于或少于4个十六进制数字，请将该值放在大括号中。例如，笑的表情(😆) 是\u{1f600}
> 
> 如果需要读取或写入单个 Unicode 字符，请使用 characters 包在字符串上定义的字符 getter。返回的 Characters 对象是作为一系列 grapheme clusters 的字符串。下面是使用 characters API 的示例：

```
import 'package:characters/characters.dart';
...
var hi = 'Hi 🇩🇰';
print(hi);
print('The end of the string: ${hi.substring(hi.length - 1)}');
print('The last character: ${hi.characters.last}\n');
```

> 根据您的环境，输出如下所示：

```
$ dart bin/main.dart
Hi 🇩🇰
The end of the string: ???
The last character: 🇩🇰
```

+ Symbols

> 符号(Symbols)对象表示在 Dart 程序中声明的运算符或标识符。您可能不需要使用符号，但对于按名称引用标识符的api来说，符号是无价的，因为缩小会更改标识符名称，而不是标识符符号
> 
> 要获取标识符的符号，请使用符号字面量，# 后面紧跟标识符：

```
#radix
#bar
```

> 符号字面量是编译时常量

## 函数

> Dart 是一种真正的面向对象语言，所以即使是函数也是对象，并且有一个类型，Function。这意味着可以将函数赋值给变量或作为参数传递给其他函数。您还可以像调用函数一样调用 Dart 类的实例
> 
> 下面是实现函数的示例：

```
bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```

> 尽管 Effective  Dart 建议对公共 api 使用类型注释，但是如果省略以下类型，该函数仍然可以工作：

```
isNoble(atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```

> 对于只包含一个表达式的函数，可以使用速记语法：

```
bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
```

> =>expr 语法是 {return expr；} 的简写。=> 符号有时被称为箭头语法
> 
> 注意：在箭头（=>）和分号（；）之间只能出现不是语句的表达式。例如，不能将 if 语句放在那里，但可以使用条件表达式
> 
> 函数可以有两种类型的参数：必选参数和可选参数。首先列出必选参数，然后列出所有可选参数。可选参数可以是命名参数或位置参数
> 
> 注意：一些API（特别是 Flutter 小部件构造函数）只使用命名参数，即使对于必选参数也是如此

+ 可选参数

> 可选参数可以是命名参数或位置参数，但不能同时是两者
 
+ 命名参数

> 调用函数时，可以使用 paramName:value 指定命名参数。例如：

```
enableFlags(bold: true, hidden: false);
```

> 定义函数时，使用 {param1，param2，…} 指定命名参数：

```
/// Sets the [bold] and [hidden] flags ...
void enableFlags({bool bold, bool hidden}) {...}
```

> 尽管命名参数是一种可选参数，但您可以使用 @required 对其进行注释，以指示该参数是必需的，即用户必须为该参数提供一个值。例如：

```
const Scrollbar({Key key, @required Widget child})
```

> 如果试图在不指定 child 的情况下创建滚动条，那么分析器将报告这个问题
> 
> 要使用 @required 注释，依赖于 meta 包并导入 package:meta/meta.dart

+ 位置参数

> 在[]中包装一组函数参数将它们标记为可选位置参数：

```
String say(String from, String msg, [String device]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  return result;
}
```

> 下面是不使用可选参数调用此函数的示例：

```
assert(say('Bob', 'Howdy') == 'Bob says Howdy');
```

> 下面是使用第三个参数调用此函数的示例：

```
assert(say('Bob', 'Howdy', 'smoke signal') ==
    'Bob says Howdy with a smoke signal');
```

+ 默认参数值

> 函数可以使用 = 为命名参数和位置参数定义默认值。默认值必须是编译时常量。如果未提供默认值，则默认值为空
> 
> 下面是为命名参数设置默认值的示例：

```
/// Sets the [bold] and [hidden] flags ...
void enableFlags({bool bold = false, bool hidden = false}) {...}

// bold will be true; hidden will be false.
enableFlags(bold: true);
```

> 注意弃用：旧代码可能使用冒号（：）而不是 = 来设置命名参数的默认值。原因是最初仅 ：支持命名参数。这种支持可能被弃用，因此我们建议您使用 = 来指定默认值
> 
> 下一个示例显示如何设置位置参数的默认值：

```
String say(String from, String msg,
    [String device = 'carrier pigeon', String mood]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  if (mood != null) {
    result = '$result (in a $mood mood)';
  }
  return result;
}

assert(say('Bob', 'Howdy') ==
    'Bob says Howdy with a carrier pigeon');
```

> 也可以将 list 或 map 作为默认值传递。下面的示例定义了一个函数 doStuff（），该函数指定 list 参数的默认 list 和 gifts 参数的默认 map

```
void doStuff(
    {List<int> list = const [1, 2, 3],
    Map<String, String> gifts = const {
      'first': 'paper',
      'second': 'cotton',
      'third': 'leather'
    }}) {
  print('list:  $list');
  print('gifts: $gifts');
}
```

+ main() 函数

> 每个应用程序都必须有一个顶级 main（）函数，该函数用作应用程序的入口点。函数的作用是：返回 void，参数有一个可选的 List<String> 参数
> 
> 下面是 web 应用程序的 main（）函数示例：

```
void main() {
  querySelector('#sample_text_id')
    ..text = 'Click me!'
    ..onClick.listen(reverseText);
}
```

> 注：前述代码中的 .. 语法称为级联。通过级联，可以对单个对象的成员执行多个操作
> 
> 下面是一个命令行应用程序的 main（）函数的示例，它接受参数：

```
// Run the app like this: dart args.dart 1 test
void main(List<String> arguments) {
  print(arguments);

  assert(arguments.length == 2);
  assert(int.parse(arguments[0]) == 1);
  assert(arguments[1] == 'test');
}
```

> 可以使用 args 库定义和分析命令行参数

+ 作为一级对象的函数

> 可以将函数作为参数传递给另一个函数。例如：

```
void printElement(int element) {
  print(element);
}

var list = [1, 2, 3];

// Pass printElement as a parameter.
list.forEach(printElement);
```

> 也可以将函数分配给变量，例如：

```
var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
assert(loudify('hello') == '!!! HELLO !!!');
```

+ 匿名函数

> 大多数函数都是命名的，例如 main（）或 printElement（）。还可以创建匿名函数，有时也称为 lambda 或闭包
> 
> 可以将匿名函数分配给变量，以便可以从集合中添加或移除它
> 
> 匿名函数看起来类似于命名函数-括号之间有零个或多个参数，由逗号和可选类型注释分隔
> 
> 下面的代码块包含函数体：

```
([[Type] param1[, …]]) { 
  codeBlock; 
}; 
```

> 下面的示例使用非类型化参数 item 定义匿名函数。
> 
> 这个方法（为 list 中的没一项调用）打印相应索引对应项目中的字符串

```
var list = ['apples', 'bananas', 'oranges'];
list.forEach((item) {
  print('${list.indexOf(item)}: $item');
});
```

> 如果函数只包含一个语句，则可以使用箭头符号将其缩短

```
list.forEach(
    (item) => print('${list.indexOf(item)}: $item'));
```

+ 词法范围(Lexical scope)

> Dart 是一种词汇范围的语言，这意味着变量的范围是静态确定的，只是由代码的布局决定的。您可以“沿着大括号向外”查看变量是否在范围内
> 
> 下面是在每个作用域级别都有变量的嵌套函数示例：

```
bool topLevel = true;

void main() {
  var insideMain = true;

  void myFunction() {
    var insideFunction = true;

    void nestedFunction() {
      var insideNestedFunction = true;

      assert(topLevel);
      assert(insideMain);
      assert(insideFunction);
      assert(insideNestedFunction);
    }
  }
}
```

> 注意 nestedFunction（）如何使用从各个级别到顶层的变量

+ 词法闭包(Lexical closures)

> 闭包是一个函数对象，它可以访问其词法范围内的变量，即使该函数在其原始范围之外使用
> 
> 函数可以关闭在周围作用域中定义的变量。在下面的示例中，makeAdder（）捕获变量 addBy。无论返回的函数走到哪里，它都会记住 addBy

```
/// Returns a function that adds [addBy] to the
/// function's argument.
Function makeAdder(num addBy) {
  return (num i) => addBy + i;
}

void main() {
  // Create a function that adds 2.
  var add2 = makeAdder(2);

  // Create a function that adds 4.
  var add4 = makeAdder(4);

  assert(add2(3) == 5);
  assert(add4(3) == 7);
}
```

+ 测试函数是否相等

> 下面是测试顶级函数、静态方法和实例方法是否相等的示例：

```
void foo() {} // A top-level function

class A {
  static void bar() {} // A static method
  void baz() {} // An instance method
}

void main() {
  var x;

  // Comparing top-level functions.
  x = foo;
  assert(foo == x);

  // Comparing static methods.
  x = A.bar;
  assert(A.bar == x);

  // Comparing instance methods.
  var v = A(); // Instance #1 of A
  var w = A(); // Instance #2 of A
  var y = w;
  x = w.baz;

  // These closures refer to the same instance (#2),
  // so they're equal.
  assert(y.baz == x);

  // These closures refer to different instances,
  // so they're unequal.
  assert(v.baz != w.baz);
}
```

+ 返回值

> 所有函数都返回一个值。如果未指定返回值，则语句返回 null；隐式附加到函数体

```
foo() {}

assert(foo() == null);
```

## 运算符

> Dart 定义了下表中所示的运算符。可以重写这些运算符中的许多
> 
> 一元后缀 : expr++    expr--    ()    []    .    ?.
> 
> 一元前缀 : -expr    !expr    ~expr    ++expr    --expr      await expr 
> 
> 乘法的 : *    /    %  ~/
> 
> 加法的 : +    -
> 
> 移位 : <<    >>    >>>
> 
> 按位与 : &
> 
> 位异或 : ^
> 
> 按位或 : |
> 
> 关系和类型测试 : >=    >    <=    <    as    is    is!
> 
> 相等 : ==    !=   
> 
> 逻辑与 : &&
> 
> 逻辑或 : ||
> 
> 如果为空 : ??
> 
> 有条件的 : expr1 ? expr2 : expr3
> 
> 级联 : ..
> 
> 赋值 : =    *=    /=   +=   -=   &=   ^=   etc.
> 
> 使用运算符时，将创建表达式。下面是一些运算符表达式的示例：

```
a++
a + b
a = b
a == b
c ? a : b
a is T
```

> 在运算符表中，每个运算符的优先级都高于其后面行中的运算符。例如，乘法运算符 % 的优先级高于相等运算符 ==，后者的优先级高于逻辑运算符 &&。这种优先级意味着以下两行代码的执行方式相同：

```
// Parentheses improve readability.
if ((n % i == 0) && (d % i == 0)) ...

// Harder to read, but equivalent.
if (n % i == 0 && d % i == 0) ...
```

> 警告：对于在两个操作数上工作的运算符，最左边的操作数决定使用哪个版本的运算符。例如，如果有 Vector 对象和 Point 对象，aVector + aPoint 使用 Vector 版本的 +

+ 算术运算符

> Dart 支持常用的算术运算符，如下表所示：
> 
> + : 加
> 
> - : 减
> 
> -expr : 一元减号，也称为否定（颠倒表达式的符号）
> 
> * : 乘
> 
> / : 除
> 
> ~/ : 除法，返回整数结果
> 
> % : 获取整数除法（模）的余数
> 
> 例子：

```
assert(2 + 3 == 5);
assert(2 - 3 == -1);
assert(2 * 3 == 6);
assert(5 / 2 == 2.5); // Result is a double
assert(5 ~/ 2 == 2); // Result is an int
assert(5 % 2 == 1); // Remainder

assert('5/2 = ${5 ~/ 2} r ${5 % 2}' == '5/2 = 2 r 1');
```

> Dart还支持前缀和后缀递增和递减运算符
> 
> ++var : var = var + 1 (expression value is var + 1)
> 
> var++ : var = var + 1 (expression value is var)
> 
> --var : var = var – 1 (expression value is var – 1)
> 
> var-- : var = var – 1 (expression value is var)
> 
> 例子：

```
var a, b;

a = 0;
b = ++a; // Increment a before b gets its value.
assert(a == b); // 1 == 1

a = 0;
b = a++; // Increment a AFTER b gets its value.
assert(a != b); // 1 != 0

a = 0;
b = --a; // Decrement a before b gets its value.
assert(a == b); // -1 == -1

a = 0;
b = a--; // Decrement a AFTER b gets its value.
assert(a != b); // -1 != 0
```

+ 等式和关系运算符

> 下表列出了相等运算符和关系运算符的含义
> 
> == : 相等；参见下面的讨论
> 
> != : 不相等
> 
> `>` : 大于
> 
> < : 小于
> 
> `>=` : 大于或等于
> 
> <= : 小于或等于
> 
> 要测试两个对象 x 和 y 是否表示同一事物，请使用 == 运算符。（在少数需要知道两个对象是否完全相同的情况下，请改用 identical（）函数。）== 运算符的工作原理如下：
> 
> 1.如果 x 或 y 为空，如果都为空，则返回 true；如果只有一个为空，则返回 false
> 
> 2.返回方法调用的结果x.=（y）.
> 
> 下面是使用等式和关系运算符的示例：

```
assert(2 == 2);
assert(2 != 3);
assert(3 > 2);
assert(2 < 3);
assert(3 >= 3);
assert(2 <= 3);
```

+ 类型测试运算符

> as : 类型转换（也用于指定库前缀）
> 
> is : 如果对象具有指定类型，则为 True
> 
> is! : 如果对象具有指定类型，则为False
> 
> 如果 obj 实现 T 指定的接口，则 obj is T 的结果为 true。例如，obj is Object始终为 true。使用 as 运算符将对象强制转换为特定类型，前提是并且仅当您确定该对象属于该类型时。例子：

```
(emp as Person).firstName = 'Bob';
```

> 如果不确定对象的类型是 T，则在使用对象之前使用 is T 检查该类型

```
if (emp is Person) {
  // Type check
  emp.firstName = 'Bob';
}
```

> 注意：上述代码不等价。如果 emp 为空或不是一个 Person，第一个示例抛出一个异常；第二个示例什么也不做

+ 赋值运算符

> 正如您已经看到的，您可以使用 = 运算符赋值。若要仅在赋值给变量为空时赋值，请使用 ??= 操作符

```
// Assign value to a
a = value;
// Assign value to b if b is null; otherwise, b stays the same
b ??= value;
```

> 复合赋值运算符，如 += 将操作与赋值结合起来
> 
> 下面的示例使用赋值运算符和复合赋值运算符：

```
var a = 2; // Assign using =
a *= 3; // Assign and multiply: a = a * 3
assert(a == 6);
```

+ 逻辑运算符

> 可以使用逻辑运算符反转或组合布尔表达式
> 
> !expr : 反转以下表达式（将 false 更改为 true，反之亦然）
> 
> || : 逻辑或
> 
> && : 逻辑与
> 
> 下面是使用逻辑运算符的示例：

```
if (!done && (col == 0 || col == 3)) {
  // ...Do something...
}
```

+ 位和移位运算符

> 可以操纵 Dart 中的整数的个别数字位。通常，将这些位和移位运算符与整数一起使用
> 
> & : AND
> 
> | : OR
> 
> ^ : XOR
> 
> ~expr : 一元逐位补码（0变成1；1变成0）
> 
> << : 左移
> 
> `>>` : 右移
> 
> 下面是使用位和移位运算符的示例：

```
final value = 0x22;
final bitmask = 0x0f;

assert((value & bitmask) == 0x02); // AND
assert((value & ~bitmask) == 0x20); // AND NOT
assert((value | bitmask) == 0x2f); // OR
assert((value ^ bitmask) == 0x2d); // XOR
assert((value << 4) == 0x220); // Shift left
assert((value >> 4) == 0x02); // Shift right
```

+ 条件表达式

> Dart 有两个运算符，可简洁地计算需要 if-else 语句的表达式：
> 
> *condition ? expr1 : expr2*
> 
> 如果 condition 为 true，则计算 expr1（并返回其值）；否则，计算并返回 expr2 的值
> 
> *expr1 ?? expr2*
> 
> 如果 expr1 为非空，则返回其值；否则，计算并返回 expr2 的值
> 
> 当需要基于布尔表达式赋值时，考虑使用 ？:

```
var visibility = isPublic ? 'public' : 'private';
```

> 如果布尔表达式测试为空，请考虑使用？？.

```
String playerName(String name) => name ?? 'Guest';
```

> 上一个例子至少可以用另外两种方式来编写，但不是那么简洁：

```
// Slightly longer version uses ?: operator.
String playerName(String name) => name != null ? name : 'Guest';

// Very long version uses if-else statement.
String playerName(String name) {
  if (name != null) {
    return name;
  } else {
    return 'Guest';
  }
}
```

+ 级联符号（…）

> 级联（..）允许您对同一对象执行一系列操作。除了函数调用之外，还可以访问同一对象上的字段。这通常节省了创建临时变量的步骤，并允许您编写更流畅的代码
> 
> 请考虑以下代码：

```
querySelector('#confirm') // Get an object.
  ..text = 'Confirm' // Use its members.
  ..classes.add('important')
  ..onClick.listen((e) => window.alert('Confirmed!'));
```

> 第一个方法调用 querySelector（）返回选择器对象。遵循级联表示法的代码在此选择器对象上操作，忽略可能返回的任何后续值
> 
> 前面的例子相当于：

```
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
```

> 级联可以嵌套使用：

```
final addressBook = (AddressBookBuilder()
      ..name = 'jenny'
      ..email = 'jenny@example.com'
      ..phone = (PhoneNumberBuilder()
            ..number = '415-555-0100'
            ..label = 'home')
          .build())
    .build();
```

> 小心在返回实际对象的函数上构造级联。例如，以下代码失败:

```
var sb = StringBuffer();
sb.write('foo')
  ..write('bar'); // Error: method 'write' isn't defined for 'void'.
```

> 调用 sb.write（）返回 void，所以不能在 void 上构造级联
> 
> 注意：严格来说，级联的“双点”符号不是运算符。这只是 Dart 语法的一部分
> 
+ 其他运算符

> 您已经在其他示例中看到了大多数剩余的运算符：
> 
> () ： 表示函数调用
> 
> [] ： 列表访问，引用列表中指定索引处的值
> 
> . ： 成员访问，引用表达式的属性；例如：foo.bar从表达式foo中选择属性栏
> 
> ?. ： 条件成员访问，类似.，但最左边的操作数可以为空；例如：foo？.bar从表达式foo中选择属性bar，除非foo为空（在这种情况下，foo?.bar 为空）

## 控制流语句

> 可以使用以下任一方法控制 Dart 代码的流动：

+ If and else
 
> Dart 支持 if 语句和可选的 else 语句，如下例所示：

```
if (isRaining()) {
  you.bringRainCoat();
} else if (isSnowing()) {
  you.wearJacket();
} else {
  car.putTopDown();
}
```

> 与 JavaScript 不同，条件必须使用布尔值，而不是其他值
 
+ For loops
 
> 可以使用标准 for 循环进行迭代。例如：

```
var message = StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
  message.write('!');
}
```

> Dart 的 for 循环中的闭包捕获索引的值，避免了 JavaScript 中常见的陷阱。例如：

```
var callbacks = [];
for (var i = 0; i < 2; i++) {
  callbacks.add(() => print(i));
}
callbacks.forEach((c) => c());
```

> 如预期，输出为 0，然后是 1。相反，该示例将在 JavaScript 中打印 2 和 2
> 
> 如果要迭代的对象是 Iterable，则可以使用 forEach（）方法。如果不需要知道当前迭代计数器，则使用 forEach（）是一个不错的选择：

```
candidates.forEach((candidate) => candidate.interview());
```

> 诸如 List 和 Set 之类的可 Iterable 类也支持for-in 的迭代形式：

```
var collection = [0, 1, 2];
for (var x in collection) {
  print(x); // 0 1 2
}
```

+ While and do-while

> while 循环计算循环之前的条件：

```
while (!isDone()) {
  doSomething();
}
```

> do-while 循环计算循环后的条件：

```
do {
  printLine();
} while (!atEndOfPage());
```

+ Break and continue

> 使用 break 停止循环：

```
while (true) {
  if (shutDownRequested()) break;
  processIncomingRequests();
}
```

> 使用 continue 跳到下一个循环迭代：

```
for (int i = 0; i < candidates.length; i++) {
  var candidate = candidates[i];
  if (candidate.yearsExperience < 5) {
    continue;
  }
  candidate.interview();
}
```

> 如果使用 Iterable（如 list 或 set ），则可以用不同的方式编写该示例：

```
candidates
    .where((c) => c.yearsExperience >= 5)
    .forEach((c) => c.interview());
```

+ Switch and case

> Dart 中的 Switch 语句使用 == 比较整数、字符串或编译时常量。比较的对象必须都是同一个类（而不是其任何子类型）的实例，并且该类不能重写 ==。枚举类型在 switch 语句中工作良好
> 
> 注意：Dart 中的 Switch 语句用于有限的情况，例如在解释器或扫描仪中
> 
> 通常，每个非空 case 子句都以 break 语句结束。结束非空 case 子句的其他有效方法是 continue、throw 或 return 语句
> 
> 当没有 case 子句匹配时，使用 default 子句执行代码：

```
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    executeClosed();
    break;
  case 'PENDING':
    executePending();
    break;
  case 'APPROVED':
    executeApproved();
    break;
  case 'DENIED':
    executeDenied();
    break;
  case 'OPEN':
    executeOpen();
    break;
  default:
    executeUnknown();
}
```

> 以下示例省略 case 子句中的 break 语句，从而生成错误：

```
var command = 'OPEN';
switch (command) {
  case 'OPEN':
    executeOpen();
    // ERROR: Missing break

  case 'CLOSED':
    executeClosed();
    break;
}
```

> 但是，Dart 确实支持空 case 子句，允许一种形式的 fall-through：

```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED': // Empty case falls through.
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```

> 如果您真的希望 fall-through，可以使用 continue 语句和标签：

```
var command = 'CLOSED';
switch (command) {
  case 'CLOSED':
    executeClosed();
    continue nowClosed;
  // Continues executing at the nowClosed label.

  nowClosed:
  case 'NOW_CLOSED':
    // Runs for both CLOSED and NOW_CLOSED.
    executeNowClosed();
    break;
}
```

> case 子句可以有局部变量，这些变量只在该子句的范围内可见

+ Assert

> 在开发过程中，使用 assert 语句 - assert（condition，optionalMessage）；- 如果布尔条件为 false，则中断正常执行。可以在本教程中找到 assert 语句的示例。这里还有一些：

```
// Make sure the variable has a non-null value.
assert(text != null);

// Make sure the value is less than 100.
assert(number < 100);

// Make sure this is an https URL.
assert(urlString.startsWith('https'));
```

> 若要将消息附加到 assert，请添加字符串作为 assert 的第二个参数

```
assert(urlString.startsWith('https'),
    'URL ($urlString) should start with "https".');
```

> assert 的第一个参数可以是解析为布尔值的任何表达式。如果表达式的值为true，则 assert 成功并继续执行。如果为false，则 assert 失败并引发异常（AssertionError）
> 
> assert 到底什么时候起作用？这取决于您使用的工具和框架：
> 
> Flutter 的调试模式启动断言
> 
> 默认情况下，开发专用工具（如 dartdevc ）通常启用断言
> 
> 一些工具（如 dart 和 dart2js ）通过命令行标志支持断言：--enable-asserts
> 
> 在生产代码中，断言被忽略，断言的参数不被计算

+ Exceptions

> Dart 代码可以抛出和捕获异常。异常是指指示意外发生的错误。如果未捕获异常，则引发异常的 isolate 将挂起，通常 isolate 及其程序将终止
> 
> 与 Java 相反，Dart 的所有异常都是未检查的异常。方法不声明它们可能抛出哪些异常，也不要求您捕获任何异常
> 
> Dart 提供 Exception 和 Error 类型以及许多预定义的子类型。当然，您可以定义自己的异常。但是，Dart 程序可以抛出任何非空对象，而不仅仅是 Exception 和 Error 对象作为异常

+ Throw

> 下面是抛出或引发异常的示例：

```
throw FormatException('Expected at least 1 section');
```

> 也可以抛出任意对象：

```
throw 'Out of llamas!';
```

> 注意：Production-quality 代码通常抛出实现 Error 或 Exception 的类型
> 
> 因为抛出异常是一个表达式，所以可以在 => 语句中抛出异常，也可以在允许表达式的任何其他地方抛出异常：

```
void distanceTo(Point other) => throw UnimplementedError();
```

+ Catch

> 捕获或捕获异常会阻止异常传播（除非重新引发异常）。捕捉异常可以让您有机会处理它：

```
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  buyMoreLlamas();
}
```

> 要处理可以引发多个异常类型的代码，可以指定多个 catch 子句。与抛出对象的类型匹配的第一个 catch 子句处理异常。如果 catch 子句未指定类型，则该子句可以处理任何类型的抛出对象：

```
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  // A specific exception
  buyMoreLlamas();
} on Exception catch (e) {
  // Anything else that is an exception
  print('Unknown exception: $e');
} catch (e) {
  // No specified type, handles all
  print('Something really unknown: $e');
}
```

> 如前面的代码所示，您可以使用 on 或 catch，也可以同时使用两者。需要指定异常类型时使用 on。当异常处理程序需要异常对象时使用 catch
> 
> 可以为 catch（） 指定一个或两个参数。第一个是抛出的异常，第二个是堆栈跟踪（stack trace 对象）

```
try {
  // ···
} on Exception catch (e) {
  print('Exception details:\n $e');
} catch (e, s) {
  print('Exception details:\n $e');
  print('Stack trace:\n $s');
}
```

> 要在允许传播异常的同时部分处理该异常，请使用 rethrow 关键字

```
void misbehave() {
  try {
    dynamic foo = true;
    print(foo++); // Runtime error
  } catch (e) {
    print('misbehave() partially handled ${e.runtimeType}.');
    rethrow; // Allow callers to see the exception.
  }
}

void main() {
  try {
    misbehave();
  } catch (e) {
    print('main() finished handling ${e.runtimeType}.');
  }
}
```

+ Finally

> 要确保无论是否引发异常，都会运行某些代码，请使用 finally 子句。如果没有 catch 子句与异常匹配，则在 finally 子句运行后传播异常：

```
try {
  breedMoreLlamas();
} finally {
  // Always clean up, even if an exception is thrown.
  cleanLlamaStalls();
}
```

> finally 子句在任何匹配的 catch 子句之后运行：

```
try {
  breedMoreLlamas();
} catch (e) {
  print('Error: $e'); // Handle the exception first.
} finally {
  cleanLlamaStalls(); // Then clean up.
}
```

## 类

+ Dart 是一种面向对象的语言，具有类和 mixin-based 的继承。每个对象都是一个类的实例，所有类都是从对象派生的。mixin-based 的继承意味着尽管每个类（除了 Object ）只有一个超类，但一个类体可以在多个类层次结构中重用。Extension methods 是在不更改类或创建子类的情况下向类添加功能的一种方法

+ 使用类成员

> 对象有由函数和数据（分别是方法和实例变量）组成的成员。当您调用一个方法时，您可以在一个对象上调用它：该方法可以访问该对象的函数和数据
> 
> 使用点（.）引用实例变量或方法：

```
var p = Point(2, 2);

// Set the value of the instance variable y.
p.y = 3;

// Get the value of y.
assert(p.y == 3);

// Invoke distanceTo() on p.
num distance = p.distanceTo(Point(4, 4));
```

> 使用 ?. 而不是 . 来避免最左边的操作数为空时出现异常：

```
// If p is non-null, set its y value to 4.
p?.y = 4;
```

+ 使用构造函数

> 可以使用构造函数创建对象。构造函数名称可以是 ClassName 或 ClassName.identifier。例如，以下代码使用 Point（）和 Point.fromJson（）构造函数创建 Point 对象：

```
var p1 = Point(2, 2);
var p2 = Point.fromJson({'x': 1, 'y': 2});
```

> 以下代码具有相同的效果，但在构造函数名称之前使用可选的 new 关键字：

```
var p1 = new Point(2, 2);
var p2 = new Point.fromJson({'x': 1, 'y': 2});
```

> 版本说明：new 关键字在 Dart 2 中变为可选
> 
> 有些类提供常量构造函数。要使用常量构造函数创建编译时常量，请将 const 关键字放在构造函数名称之前：

```
var p = const ImmutablePoint(2, 2);
```

> 构造两个相同的编译时常量将导致一个规范实例：

```
var a = const ImmutablePoint(1, 1);
var b = const ImmutablePoint(1, 1);

assert(identical(a, b)); // They are the same instance!
```

> 在常量上下文中，可以在构造函数或文本之前省略 const。例如，看看这段代码，它创建了一个常量 map：

```
// Lots of const keywords here.
const pointAndLine = const {
  'point': const [const ImmutablePoint(0, 0)],
  'line': const [const ImmutablePoint(1, 10), const ImmutablePoint(-2, 11)],
};
```

> 除了第一个 const 关键字外，您可以省略其他所有 const：

```
// Only one const, which establishes the constant context.
const pointAndLine = {
  'point': [ImmutablePoint(0, 0)],
  'line': [ImmutablePoint(1, 10), ImmutablePoint(-2, 11)],
};
```

> 如果常量构造函数不在常量上下文中且在不使用常量的情况下调用，则它将创建一个非常量对象：

```
var a = const ImmutablePoint(1, 1); // Creates a constant
var b = ImmutablePoint(1, 1); // Does NOT create a constant

assert(!identical(a, b)); // NOT the same instance!
```

> 版本说明：const 关键字在 Dart 2 中的常量上下文中变为可选

+ 获取对象类型

> 若要在运行时获取对象的类型，可以使用对象的 runtimeType 属性，该属性返回类型对象

```
print('The type of a is ${a.runtimeType}');
```

+ 实例变量

> 下面是声明实例变量的方法：

```
class Point {
  num x; // Declare instance variable x, initially null.
  num y; // Declare y, initially null.
  num z = 0; // Declare z, initially 0.
}
```

> 所有未初始化的实例变量的值都为空
> 
> 所有实例变量都生成隐式 getter 方法。非最终实例变量还生成隐式 setter 方法

```
class Point {
  num x;
  num y;
}

void main() {
  var point = Point();
  point.x = 4; // Use the setter method for x.
  assert(point.x == 4); // Use the getter method for x.
  assert(point.y == null); // Values default to null.
}
```

> 如果在声明实例变量的位置（而不是在构造函数或方法中）初始化实例变量，则在创建实例时设置该值，即在构造函数及其初始值设定项列表执行之前

+ 构造函数

> 通过创建与其类同名的函数（加上命名构造函数中描述的附加标识符）来声明构造函数。最常见的构造函数形式生成构造函数创建类的新实例：

```
class Point {
  num x, y;

  Point(num x, num y) {
    // There's a better way to do this, stay tuned.
    this.x = x;
    this.y = y;
  }
}
```

> this 关键字引用当前实例
> 
> 注意：仅当存在名称冲突时才使用 this。否则，Dart 样式会忽略 this
> 
> 将构造函数参数分配给实例变量的模式非常常见，因此 Dart 具有语法糖使其更容易：

```
class Point {
  num x, y;

  // Syntactic sugar for setting x and y
  // before the constructor body runs.
  Point(this.x, this.y);
}
```

+ 默认构造函数

> 如果不声明构造函数，则会为您提供默认构造函数。默认构造函数没有参数，并调用超类中的无参数构造函数

+ 构造函数不是继承的

> 子类不会从其超类继承构造函数。声明没有构造函数的子类只有默认（没有参数，没有名称）构造函数

+ 命名构造函数

> 使用命名构造函数为类实现多个构造函数或提供额外的清晰度：

```
class Point {
  num x, y;

  Point(this.x, this.y);

  // Named constructor
  Point.origin() {
    x = 0;
    y = 0;
  }
}
```

> 请记住，构造函数不能被继承，这意味着超类的命名构造函数不能被子类继承。如果要使用在超类中定义的命名构造函数创建子类，则必须在子类中实现该构造函数

+ 调用非默认超类构造函数

> 默认情况下，子类中的构造函数调用超类的未命名的无参数构造函数。超类的构造函数在构造函数体的开头调用。如果同时使用初始值设定项列表(initializer list)，则在调用超类之前执行该列表。总之，执行顺序如下：
> 
> 1.初始化列表(initializer list)
> 
> 2.超类的无参数构造函数
> 
> 3.主类的无参数构造函数
> 
> 如果超类没有未命名的无参数构造函数，则必须手动调用超类中的一个构造函数。在冒号（：）后面、构造函数主体（如果有）之前指定超类构造函数
> 
> 在下面的示例中，Employee 类的构造函数调用其超类 Person 的命名构造函数

```
class Person {
  String firstName;

  Person.fromJson(Map data) {
    print('in Person');
  }
}

class Employee extends Person {
  // Person does not have a default constructor;
  // you must call super.fromJson(data).
  Employee.fromJson(Map data) : super.fromJson(data) {
    print('in Employee');
  }
}

main() {
  var emp = new Employee.fromJson({});

  // Prints:
  // in Person
  // in Employee
  if (emp is Person) {
    // Type check
    emp.firstName = 'Bob';
  }
  (emp as Person).firstName = 'Bob';
}
```

> 因为超类构造函数的参数是在调用构造函数之前计算的，所以参数可以是表达式，例如函数调用：

```
class Employee extends Person {
  Employee() : super.fromJson(defaultData);
  // ···
}
```

> 警告：超类构造函数的参数没有访问权限。例如，参数可以调用静态方法，但不能调用实例方法

+ 初始化成员列表

> 除了调用超类构造函数之外，还可以在构造函数体运行之前初始化实例变量。用逗号分隔初始值设定项

```
// Initializer list sets instance variables before
// the constructor body runs.
Point.fromJson(Map<String, num> json)
    : x = json['x'],
      y = json['y'] {
  print('In Point.fromJson(): ($x, $y)');
}
```

> 在开发过程中，可以通过在初始值设定项列表中使用 assert 来验证输入

```
Point.withAssert(this.x, this.y) : assert(x >= 0) {
  print('In Point.withAssert(): ($x, $y)');
}
```

> 初始值设定项列表在设置 final 字段时非常方便。下面的示例初始化器列表中的三个 final 字段

```
import 'dart:math';

class Point {
  final num x;
  final num y;
  final num distanceFromOrigin;

  Point(x, y)
      : x = x,
        y = y,
        distanceFromOrigin = sqrt(x * x + y * y);
}

main() {
  var p = new Point(2, 3);
  print(p.distanceFromOrigin);
}
```

+ 重定向构造函数

> 有时构造函数的唯一目的是重定向到同一类中的另一个构造函数。重定向构造函数的正文为空，构造函数调用出现在冒号（：）之后

```
class Point {
  num x, y;

  // The main constructor for this class.
  Point(this.x, this.y);

  // Delegates to the main constructor.
  Point.alongXAxis(num x) : this(x, 0);
}
```

+ 常量构造函数

> 如果类生成的对象永不更改，则可以使这些对象编译时间常量。为此，定义一个 const 构造函数并确保所有实例变量都是 final

```
class ImmutablePoint {
  static final ImmutablePoint origin =
      const ImmutablePoint(0, 0);

  final num x, y;

  const ImmutablePoint(this.x, this.y);
}
```

+ 工厂构造函数

> 在实现不总是创建其类的新实例的构造函数时，请使用 factory 关键字。例如，工厂构造函数可以从缓存返回实例，也可以返回子类型的实例
> 
> 以下示例演示从缓存返回对象的工厂构造函数：

```
class Logger {
  final String name;
  bool mute = false;

  // _cache is library-private, thanks to
  // the _ in front of its name.
  static final Map<String, Logger> _cache =
      <String, Logger>{};

  factory Logger(String name) {
    return _cache.putIfAbsent(
        name, () => Logger._internal(name));
  }

  Logger._internal(this.name);

  void log(String msg) {
    if (!mute) print(msg);
  }
}
```

> 注意：工厂构造函数无法访问 this
> 
> 像调用任何其他构造函数一样调用工厂构造函数：

```
var logger = Logger('UI');
logger.log('Button clicked');
```

+ 方法

> 
> 
> 

---
# [Library tour](https://dart.dev/guides/libraries/library-tour)

---
# [Intro to Dart for Java Developers codelab](https://codelabs.developers.google.com/codelabs/from-java-to-dart)

---
# [Effective Dart](https://dart.dev/guides/language/effective-dart)

---
# [Asynchronous programming: futures, async, await](https://dart.dev/codelabs/async-await)

---
# [Asynchronous programming: streams](https://dart.dev/tutorials/language/streams)

---
# Dart
+ [Dart 官方 Docs](https://dart.dev/guides)
+ [Dart语法学习 -- *good 值得再学习*](https://www.jianshu.com/p/9e5f4c81cc7d)

## 语法要点
### 基本数据类型

> Dart 属于强类型语言(在Dart2.0之前，Dart是一门弱类型语言。2.0以后变更为强类型语言(注：官网原文是 Dart 2.0 has a sound type system))。同时属于动态类型语言(动态类型语言指只有在运行的时候才会检查数据类型，静态类型语言指编译期间就会检查数类型)，支持闭包

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
