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

> 方法是为对象提供行为的函数
> 
> *实例方法*
> 
> 对象上的实例方法可以访问实例变量和 this。下面的 distanceTo（）方法是实例方法的一个示例：

```
import 'dart:math';

class Point {
  num x, y;

  Point(this.x, this.y);

  num distanceTo(Point other) {
    var dx = x - other.x;
    var dy = y - other.y;
    return sqrt(dx * dx + dy * dy);
  }
}
```

> Getters and setters
> 
> getter 和setter 是提供对对象属性的读写访问的特殊方法。回想一下，每个实例变量都有一个隐式 getter，如果合适的话还加上一个 setter。通过使用 get 和 set 关键字实现 getter 和 setter，可以创建其他属性：

```
class Rectangle {
  num left, top, width, height;

  Rectangle(this.left, this.top, this.width, this.height);

  // Define two calculated properties: right and bottom.
  num get right => left + width;
  set right(num value) => left = value - width;
  num get bottom => top + height;
  set bottom(num value) => top = value - height;
}

void main() {
  var rect = Rectangle(3, 4, 20, 15);
  assert(rect.left == 3);
  rect.right = 12;
  assert(rect.left == -8);
}
```

> 使用 getter 和 setter，您可以从实例变量开始，然后用方法包装它们，而无需更改客户端代码
> 
> *抽象方法*
> 
> 实例、getter 和 setter 方法可以是抽象的，定义一个接口，但将其实现留给其他类。抽象方法只能存在于抽象类中
> 
> 要使方法抽象，请使用分号（；）而不是方法体：

```
abstract class Doer {
  // Define instance variables and methods...

  void doSomething(); // Define an abstract method.
}

class EffectiveDoer extends Doer {
  void doSomething() {
    // Provide an implementation, so the method is not abstract here...
  }
}
```

> *抽象类*
> 
> 使用 abstract 修饰符定义一个抽象类——一个不能实例化的类。抽象类对于定义接口非常有用，通常在某些实现中。如果希望抽象类看起来是可实例化的，请定义工厂构造函数
> 
> 抽象类通常有抽象方法。下面是声明具有抽象方法的抽象类的示例：

```
// This class is declared abstract and thus
// can't be instantiated.
abstract class AbstractContainer {
  // Define constructors, fields, methods...

  void updateChildren(); // Abstract method.
}
```

> *隐式接口*
> 
> 每个类都隐式定义一个接口，该接口包含该类及其实现的任何接口的所有实例成员。如果您想创建一个不继承 B 实现而支持 B 类 API 的类 A，那么 A 类应该实现 B 的接口
> 
> 类通过在 implements 子句中声明一个或多个接口，然后提供接口所需的 API 来实现这些接口。例如：

```
// A person. The implicit interface contains greet().
class Person {
  // In the interface, but visible only in this library.
  final _name;

  // Not in the interface, since this is a constructor.
  Person(this._name);

  // In the interface.
  String greet(String who) => 'Hello, $who. I am $_name.';
}

// An implementation of the Person interface.
class Impostor implements Person {
  get _name => '';

  String greet(String who) => 'Hi $who. Do you know who I am?';
}

String greetBob(Person person) => person.greet('Bob');

void main() {
  print(greetBob(Person('Kathy')));
  print(greetBob(Impostor()));
}
```

> 下面是一个指定类实现多个接口的示例：

```
class Point implements Comparable, Location {...}
```

+ 扩展类

> 使用 extends 创建子类，super 引用父类：

```
class Television {
  void turnOn() {
    _illuminateDisplay();
    _activateIrSensor();
  }
  // ···
}

class SmartTelevision extends Television {
  void turnOn() {
    super.turnOn();
    _bootNetworkInterface();
    _initializeMemory();
    _upgradeApps();
  }
  // ···
}
```

> *重写成员方法*
> 
> 子类可以重写实例方法、getter和setter。您可以使用@override注释来指示您有意重写成员：

```
class SmartTelevision extends Television {
  @override
  void turnOn() {...}
  // ···
}
```

> 要在类型安全的代码中缩小方法参数或实例变量的类型，可以使用 covariant 关键字

+ 可重写运算符

> 您可以覆盖下表中显示的运算符。例如，如果定义向量类，则可以定义一个+方法来添加两个向量
> 
> `<`   `+`   `|`   `[]`
> 
> `>`   `/`   `^`   `[]=`
> 
> `<=`  `~/`  `&`   `~`
> 
> `>=`  `*`   `<<`  `==`
>   
> `–`   `%`   `>>`
> 
> 注意：你可能已经注意到了 != 不是可重写的运算符。表达式 e1!=e2 只是 !（e1==e2） 的语法糖
> 
> 下面是重写 + 和 - 运算符的类的示例：

```
class Vector {
  final int x, y;

  Vector(this.x, this.y);

  Vector operator +(Vector v) => Vector(x + v.x, y + v.y);
  Vector operator -(Vector v) => Vector(x - v.x, y - v.y);

  // Operator == and hashCode not shown. For details, see note below.
  // ···
}

void main() {
  final v = Vector(2, 3);
  final w = Vector(2, 2);

  assert(v + w == Vector(4, 5));
  assert(v - w == Vector(0, 1));
}
```

> 如果重写 ==，还应该重写对象的 hashCode getter

+ noSuchMethod()

> 要在代码尝试使用不存在的方法或实例变量时检测或响应，可以重写 noSuchMethod（）：

```
class A {
  // Unless you override noSuchMethod, using a
  // non-existent member results in a NoSuchMethodError.
  @override
  void noSuchMethod(Invocation invocation) {
    print('You tried to use a non-existent member: ' +
        '${invocation.memberName}');
  }
}
```

> 除非满足以下条件之一，否则无法调用未实现的方法：
> 
> 1.接收器具有静态 dynamic 类型
> 
> 2.接收器有一个定义未实现方法的静态类型（abstract可以），接收器的动态类型有一个 noSuchMethod（）的实现，它不同于类对象中的实现

+ 扩展方法

> Dart 2.7 中引入的扩展方法是向现有库添加功能的一种方法。你甚至可以在不知情的情况下使用扩展方法。例如，当您在 IDE 中使用代码完成时，它建议将扩展方法与常规方法一起使用
> 
> 下面是在 String-api.dart 中定义的名为 parseInt（）的字符串上使用扩展方法的示例：

```
import 'string_apis.dart';
...
print('42'.padLeft(5)); // Use a String method.
print('42'.parseInt()); // Use an extension method.
```

+ 枚举类型

> 枚举类型通常称为 enumeration 或 enum，是一种特殊的类，用于表示固定数量的常量值
> 
> *使用枚举*
> 
> 使用 enum 关键字声明枚举类型：

```
enum Color { red, green, blue }
```

> 枚举中的每个值都有一个索引 getter，它返回该值在枚举声明中的从零开始的位置。例如，第一个值的索引为 0，第二个值的索引为 1

```
assert(Color.red.index == 0);
assert(Color.green.index == 1);
assert(Color.blue.index == 2);
```

> 要获取枚举中所有值的列表，请使用枚举的 values 常量

```
List<Color> colors = Color.values;
assert(colors[2] == Color.blue);
```

> 可以在 switch 语句中使用枚举，如果不处理枚举的所有值，则会收到警告：

```
var aColor = Color.blue;

switch (aColor) {
  case Color.red:
    print('Red as roses!');
    break;
  case Color.green:
    print('Green as grass!');
    break;
  default: // Without this, you see a WARNING.
    print(aColor); // 'Color.blue'
}
```

> 枚举类型具有以下限制：
> 
> 不能对枚举进行子类化、混合或实现
> 
> 不能显式实例化枚举

+ 向类添加功能：mixins

> mixin 是在多个类层次结构中重用类代码的一种方法
> 
> 要使用 mixin，请使用 with 关键字，后跟一个或多个 mixin 名称。下面的示例显示了使用 mixin 的两个类：

```
class Musician extends Performer with Musical {
  // ···
}

class Maestro extends Person
    with Musical, Aggressive, Demented {
  Maestro(String maestroName) {
    name = maestroName;
    canConduct = true;
  }
}
```

> 要实现 mixin，请创建一个扩展对象且不声明构造函数的类。除非希望 mixin 可用作常规类，否则请使用 mixin 关键字而不是类。例如：

```
mixin Musical {
  bool canPlayPiano = false;
  bool canCompose = false;
  bool canConduct = false;

  void entertainMe() {
    if (canPlayPiano) {
      print('Playing piano');
    } else if (canConduct) {
      print('Waving hands');
    } else {
      print('Humming to self');
    }
  }
}
```

> 要指定只有某些类型可以使用 mixin，例如，您的 mixin 可以调用它未定义的方法，请使用 on 指定所需的超类：

```
mixin MusicalPerformer on Musician {
  // ···
}
```

> 版本说明：Dart 2.1 中引入了对 mixin 关键字的支持。早期版本中的代码通常使用抽象类

+ 类变量和方法

> 使用 static 关键字实现类范围的变量和方法
> 
> *静态变量*
> 
> 静态变量（类变量）对于类范围的状态和常量很有用：

```
class Queue {
  static const initialCapacity = 16;
  // ···
}

void main() {
  assert(Queue.initialCapacity == 16);
}
```

> 静态变量在使用之前不会初始化
> 
> *静态方法*
> 
> 静态方法（类方法）不在实例上操作，因此无法访问该实例。例如：

```
import 'dart:math';

class Point {
  num x, y;
  Point(this.x, this.y);

  static num distanceBetween(Point a, Point b) {
    var dx = a.x - b.x;
    var dy = a.y - b.y;
    return sqrt(dx * dx + dy * dy);
  }
}

void main() {
  var a = Point(2, 2);
  var b = Point(4, 4);
  var distance = Point.distanceBetween(a, b);
  assert(2.8 < distance && distance < 2.9);
  print(distance);
}
```

> 注意：对于常用或广泛使用的实用程序和功能，考虑使用顶级函数而不是静态方法
> 
> 可以使用静态方法作为编译时常量。例如，可以将静态方法作为参数传递给常量构造函数

## 泛型

+ 如果查看基本数组类型 List 的 API 文档，您将看到该类型实际上是 List<E>。 <…> 符号将 List 标记为泛型（或参数化）类型，即具有形式类型参数的类型。按照惯例，大多数类型变量都有单字母名称，如 E、T、S、K 和 V

+ 为什么使用泛型？

> 泛型通常是类型安全所必需的，但它们比只允许代码运行更有好处：
> 
> 正确地指定泛型类型会产生更好的代码
> 
> 您可以使用泛型来减少代码重复
> 
> 如果希望列表只包含字符串，可以将其声明为 list<String>（将其读为“list of String”）。这样，您、您的程序员同事和您的工具就可以检测到，将非字符串分配给列表可能是一个错误。下面是一个例子：

```
var names = List<String>();
names.addAll(['Seth', 'Kathy', 'Lars']);
names.add(42); // Error
```

> 使用泛型的另一个原因是减少代码重复。泛型允许您在许多类型之间共享单个接口和实现，同时仍然利用静态分析。例如，假设您创建了一个用于缓存对象的接口：

```
abstract class ObjectCache {
  Object getByKey(String key);
  void setByKey(String key, Object value);
}
```

> 您发现需要此接口的字符串特定版本，因此创建另一个接口：

```
abstract class StringCache {
  String getByKey(String key);
  void setByKey(String key, String value);
}
```

> 后来，你决定你想要一个特定于数字的接口版本…你明白了
> 
> 泛型类型可以避免创建所有这些接口的麻烦。相反，您可以创建一个接受类型参数的接口：

```
abstract class Cache<T> {
  T getByKey(String key);
  void setByKey(String key, T value);
}
```

> 在这个代码中，T 是代理类型。这是一个占位符，您可以将其视为开发人员稍后将定义的类型
> 
> *使用集合字面量*
> 
> List、set 和 map 字面量可以参数化。参数化的字面量与您已经看到的字面量一样，只是在左括号之前添加了 <type>（对于 List 和 set ）或 <keyType，valueType>（对于 map）。下面是使用类型化字面量的示例：

```
var names = <String>['Seth', 'Kathy', 'Lars'];
var uniqueNames = <String>{'Seth', 'Kathy', 'Lars'};
var pages = <String, String>{
  'index.html': 'Homepage',
  'robots.txt': 'Hints for web robots',
  'humans.txt': 'We are people, not machines'
};
```

+ 对构造函数使用参数化类型

> 要在使用构造函数时指定一个或多个类型，请将这些类型放在类名后面的尖括号（<…>）中。例如：

```
var nameSet = Set<String>.from(names);
```

> 以下代码创建一个具有整数键和View类型值的 map：

```
var views = Map<int, View>();
```

+ 泛型集合及其包含的类型

> Dart 泛型类型被具体化，这意味着它们在运行时携带它们的类型信息。例如，可以测试集合的类型：

```
var names = List<String>();
names.addAll(['Seth', 'Kathy', 'Lars']);
print(names is List<String>); // true
```

> 注意：相反，Java 中的泛型使用擦除，这意味着泛型类型参数在运行时被删除。在 Java 中，您可以测试一个对象是否是 List，但不能测试它是否是 List <String>
> 
> *限制参数化类型*
> 
> 实现泛型类型时，可能需要限制其参数的类型。您可以使用 extends 执行此操作

```
class Foo<T extends SomeBaseClass> {
  // Implementation goes here...
  String toString() => "Instance of 'Foo<$T>'";
}

class Extender extends SomeBaseClass {...}
```

> 可以使用 SomeBaseClass 或其子类作为泛型参数

```
var someBaseClassFoo = Foo<SomeBaseClass>();
var extenderFoo = Foo<Extender>();
```

> 也可以不指定泛型参数

```
var foo = Foo();
print(foo); // Instance of 'Foo<SomeBaseClass>'
```

> 指定非 SomeBaseClass 类型作为泛型参数将导致错误：

```
var foo = Foo<Object>();
```

+ 使用泛型方法

> 最初，Dart 的泛型支持仅限于类。一种新的语法称为泛型方法，允许对方法和函数使用类型参数：

```
T first<T>(List<T> ts) {
  // Do some initial work or error checking, then...
  T tmp = ts[0];
  // Do some additional checking or processing...
  return tmp;
}
```

> 这里，first（<T>）上的泛型类型参数允许您在几个地方使用类型参数 T：
> 
> 在函数的返回类型（T）中
> 
> 在参数类型中（List<T>）
> 
> 在局部变量类型（T tmp）中

## 库和可见性

> import 和 library 指令可以帮助您创建模块化的、可共享的代码库。库不仅提供 API，而且是一个隐私单元：以下划线（_）开头的标识符只在库中可见。每个 Dart 应用程序都是一个库，即使它不使用 library 指令
> 
> 可以使用包分发库

+ 使用库

> 使用 import 指定如何在另一个库的作用域中使用一个库中的命名空间
> 
> 例如，Dart web 应用程序通常使用 Dart:html 库，它们可以如下方式导入该库：

```
import 'dart:html';
```

> 唯一需要导入的参数是指定库的 URI。对于内置库，URI 具有特殊的 dart: 方案。对于其他库，可以使用文件系统路径或 package：方案。package: 方案指定由包管理器（如 pub 工具）提供的库。例如：

```
import 'package:test/test.dart';
```

+ 指定库前缀

> 如果导入两个具有冲突标识符的库，则可以为一个或两个库指定前缀。例如，如果 library1 和 library2 都有一个 Element 类，那么您可能有如下代码：

```
import 'package:lib1/lib1.dart';
import 'package:lib2/lib2.dart' as lib2;

// Uses Element from lib1.
Element element1 = Element();

// Uses Element from lib2.
lib2.Element element2 = lib2.Element();
```

+ 仅导入库的一部分

> 如果只想使用库的一部分，可以有选择地导入库。例如：

```
// Import only foo.
import 'package:lib1/lib1.dart' show foo;

// Import all names EXCEPT foo.
import 'package:lib2/lib2.dart' hide foo;
```

+ 库的懒加载

> 延迟加载（也称为懒加载）允许web应用在需要库时按需加载库。下面是一些可能使用延迟加载的情况：
> 
> 减少 web 应用的初始启动时间
> 
> 执行 A/B 测试尝试算法的替代实现
> 
> 加载很少使用的功能，如可选屏幕和对话框
> 
> 要延迟加载库，必须首先使用 deferred as 导入它

```
import 'package:greetings/hello.dart' deferred as hello;
```

> 当需要库时，使用库的标识符调用 loadLibrary（）

```
Future greet() async {
  await hello.loadLibrary();
  hello.printGreeting();
}
```

> 在前面的代码中，await 关键字暂停执行，直到加载库。可以在库上多次调用 loadLibrary（），而不会出现问题。库只加载一次
> 
> 使用延迟加载时请记住以下内容：
> 
> 延迟库的常量不是导入文件中的常量。记住，在加载延迟库之前，这些常量是不存在的
> 
> 不能在导入文件中使用延迟库中的类型。相反，请考虑将接口类型移动到由延迟库和导入文件导入的库中
> 
> Dart隐式地将loadLibrary（）插入到使用deferred as namespace定义的命名空间中。函数的作用是：返回一个 Future

## 异步支持

> Dart 库充满了返回 Future 对象或 Stream 对象的函数。这些函数是异步的：它们在设置一个可能耗时的操作（如 I/O ）之后返回，而不等待该操作完成
> 
> async 和 await 关键字支持异步编程，允许您编写类似于同步代码的异步代码

+ 处理 Future

> 当你需要一个完成的 Future 的结果时，你有两个选择：
> 
> 使用 async 和 await
> 
> 使用 Future 的 API
> 
> 使用 async 和 await 的代码是异步的，但看起来很像同步代码。例如，下面的一些代码使用 await 来等待异步函数的结果：

```
await lookUpVersion();
```

> 要使用 await，代码必须在异步函数中—标记为 async 的函数：

```
Future checkVersion() async {
  var version = await lookUpVersion();
  // Do something with version
}
```

> 注意：尽管异步函数可能执行耗时的操作，但它不会等待这些操作。相反，异步函数只在遇到第一个 await 表达式之前执行。然后它返回一个 Future 对象，仅在 await 表达式完成后才继续执行
> 
> 使用 try、catch 和 finally 在使用 await 的代码中处理错误和清理：

```
try {
  version = await lookUpVersion();
} catch (e) {
  // React to inability to look up the version
}
```

> 可以在异步函数中多次使用 await。例如，以下代码将三次 await 函数的结果：

```
var entrypoint = await findEntrypoint();
var exitCode = await runExecutable(entrypoint, args);
await flushThenExit(exitCode);
```

> 在 await 表达式中，表达式的值通常是 Future；如果不是，则该值将自动包装在 Future 中。这个 Future 对象表示返回一个对象的承诺。await 表达式的值是返回的对象。await 表达式使执行暂停，直到该对象可用为止
> 
> 如果在使用 await 时遇到编译时错误，请确保 await 在 async 函数中。例如，要在应用程序的 main（）函数中使用 await，main（）的主体必须标记为 async：

```
Future main() async {
  checkVersion();
  print('In main: version is ${await lookUpVersion()}');
}
```

+ 声明 async 函数

> async 函数是其主体用 async 修饰符标记的函数
> 
> 向函数中添加 async 关键字将使其返回 Future。例如，考虑这个同步函数，它返回一个字符串：

```
String lookUpVersion() => '1.0.0';
```

> 例如，如果将其更改为 async 函数，因为 Future 的实现将耗费时间，则返回的值是 Future：

```
Future<String> lookUpVersion() async => '1.0.0';
```

> 注意，函数的主体不需要使用将来的 API。如果需要，Dart 将创建 Future 对象。如果函数没有返回有用的值，请将其返回类型设为 Future<void>

+ 处理 Stream

> 当需要从 Stream 中获取值时，有两个选项：
> 
> 使用 async 和异步 for 循环（await for）
> 
> 使用 Stream  API
> 
> 注意：在使用 await for 之前，请确保它使代码更清晰，并且您确实希望等待流的所有结果。例如，对于 UI 事件监听器，通常不应该使用await for，因为 UI 框架发送无止境的事件流
> 
> 异步 for 循环具有以下形式：

```
await for (varOrType identifier in expression) {
  // Executes each time the stream emits a value.
}
```

> 表达式的值必须具有流类型。执行如下：
> 
> 1.等到流发出一个值
> 
> 2.执行 for 循环的主体，将变量设置为发出的值
> 
> 3.重复1和2直到流关闭
> 
> 若要停止侦听流，可以使用 break 或 return 语句，该语句中断 for 循环并从流中取消订阅
> 
> 如果在实现异步 for 循环时遇到编译时错误，请确保 await for 在 async 函数中。例如，要在应用程序的 main（）函数中使用异步 For 循环，main（）的主体必须标记为 async：

```
Future main() async {
  // ...
  await for (var request in requestServer) {
    handleRequest(request);
  }
  // ...
}
```

## Generators

+ 当需要惰性地生成一系列值时，请考虑使用 Generator 函数。Dart 内置了对两种 Generator 函数的支持：

> 同步 Generator：返回 Iterable 对象
> 
> 异步 Generator：返回流对象
> 
> 要实现同步 Generator 函数，请将函数体标记为 sync*，并使用 yield 语句传递值：

```
Iterable<int> naturalsTo(int n) sync* {
  int k = 0;
  while (k < n) yield k++;
}
```

> 要实现异步 Generator 函数，请将函数体标记为 async*，并使用 yield 语句传递值：

```
Stream<int> asynchronousNaturalsTo(int n) async* {
  int k = 0;
  while (k < n) yield k++;
}
```

> 如果 Generator 是递归的，则可以使用 yield* 来提高其性能：

```
Iterable<int> naturalsDownFrom(int n) sync* {
  if (n > 0) {
    yield n;
    yield* naturalsDownFrom(n - 1);
  }
}
```

## 可调用类(可调用类)

+ 要允许像函数一样调用 Dart 类的实例，请实现 call（）方法

> 在下面的示例中，WannabeFunction 类定义了一个 call（）函数，该函数接受三个字符串并将它们连接起来，每个字符串之间用空格分隔，然后附加一个感叹号

```
class WannabeFunction {
  call(String a, String b, String c) => '$a $b $c!';
}

main() {
  var wf = new WannabeFunction();
  var out = wf("Hi","there,","gang");
  print('$out');
}
```

## Isolate

> 大多数计算机，甚至在移动平台上，都有多核 CPU。为了利用所有这些内核，开发人员通常使用并发运行的共享内存线程。然而，共享状态并发很容易出错，并可能导致复杂的代码
> 
> 所有 Dart 代码都在 Isolate 内运行，而不是线程。每个 Isolate 都有自己的内存堆，确保任何其他 Isolate 都不能访问任何 Isolate 的状态

## Typedefs

> 在 Dart 中，函数是对象，就像字符串和数字是对象一样。Typedef 或函数类型别名为函数类型提供了一个名称，可以在声明字段和返回类型时使用。当 Typedef 分配给变量时，typedef 保留类型信息
> 
> 考虑以下不使用 typedef 的代码：

```
class SortedCollection {
  Function compare;

  SortedCollection(int f(Object a, Object b)) {
    compare = f;
  }
}

// Initial, broken implementation.
int sort(Object a, Object b) => 0;

void main() {
  SortedCollection coll = SortedCollection(sort);

  // All we know is that compare is a function,
  // but what type of function?
  assert(coll.compare is Function);
}
```

> 分配 f 进行比较时，类型信息丢失。f 的类型是（Object，Object）→int（这里 → 代表返回），而 compare 的类型是 Function。如果我们将代码更改为使用显式名称并保留类型信息，则开发人员和工具都可以使用该信息

```
typedef Compare = int Function(Object a, Object b);

class SortedCollection {
  Compare compare;

  SortedCollection(this.compare);
}

// Initial, broken implementation.
int sort(Object a, Object b) => 0;

void main() {
  SortedCollection coll = SortedCollection(sort);
  assert(coll.compare is Function);
  assert(coll.compare is Compare);
}
```

> 注意：目前，typedef 仅限于函数类型。我们希望这会改变
> 
> 因为 typedef 只是别名，所以它们提供了一种检查任何函数类型的方法。例如：

```
typedef Compare<T> = int Function(T a, T b);

int sort(int a, int b) => a - b;

void main() {
  assert(sort is Compare<int>); // True!
}
```

## Metadata

> 使用元数据提供有关代码的其他信息。元数据注解以字符 @ 开头，后跟对编译时常量的引用（如 deprecated ）或对常量构造函数的调用
> 
> 所有 Dart 代码都有两个注解：@deprecated 和 @override。有关使用 @override 的示例，请参见扩展类。下面是使用 @deprecated 注解的示例：

```
class Television {
  /// _Deprecated: Use [turnOn] instead._
  @deprecated
  void activate() {
    turnOn();
  }

  /// Turns the TV's power on.
  void turnOn() {...}
}
```

> 您可以定义自己的元数据注解。下面是一个定义 @todo 注解的示例，该注释包含两个参数：

```
library todo;

class Todo {
  final String who;
  final String what;

  const Todo(this.who, this.what);
}
```

> 下面是一个使用 @todo 注解的示例：

```
import 'todo.dart';

@Todo('seth', 'make this do something')
void doSomething() {
  print('do something');
}
```

> 元数据可以出现在库、类、typedef、类型参数、构造函数、工厂、函数、字段、参数或变量声明之前，也可以出现在import或export指令之前。可以在运行时使用反射检索元数据

## 注释

+ Dart 支持单行注释、多行注释和文档注释

+ 单行注释

> 单行注释以 // 开头。Dart 编译器忽略 // 和行尾之间的所有内容

```
void main() {
  // TODO: refactor into an AbstractLlamaGreetingFactory?
  print('Welcome to my Llama farm!');
}
```

+ 多行注释

> 多行注释以 `/*` 开头，以 `*/` 结尾。Dart 编译器忽略 `/*` 和 `*/` 之间的所有内容（除非注释是文档注释；请参阅下一节）。可以嵌套多行注释

```
void main() {
  /*
   * This is a lot of work. Consider raising chickens.

  Llama larry = Llama();
  larry.feed();
  larry.exercise();
  larry.clean();
   */
}
```

+ 文件注释

> 文档注释是以 /// 或 /** 开头的多行或单行注释。在连续行上使用 /// 与多行文档注释具有相同的效果
> 
> 在文档注释中，Dart 编译器忽略所有文本，除非将其括在方括号中。使用方括号，可以引用类、方法、字段、顶级变量、函数和参数。括号中的名称在文档化程序元素的词法范围内解析
> 
> 以下是引用其他类和参数的文档注释示例：

```
/// A domesticated South American camelid (Lama glama).
///
/// Andean cultures have used llamas as meat and pack
/// animals since pre-Hispanic times.
class Llama {
  String name;

  /// Feeds your llama [Food].
  ///
  /// The typical llama eats one bale of hay per week.
  void feed(Food food) {
    // ...
  }

  /// Exercises your llama with an [activity] for
  /// [timeLimit] minutes.
  void exercise(Activity activity, int timeLimit) {
    // ...
  }
}
```

> 要解析 Dart 代码并生成 HTML 文档，可以使用 SDK 的文档生成工具。

## 总结

> 本页总结了 Dart 语言中常用的功能。更多的功能正在实现中，但是我们希望它们不会破坏现有的代码

---
# [Library tour](https://dart.dev/guides/libraries/library-tour)

+ 此页显示如何使用 Dart 核心库中的主要功能。这只是一个概述，绝不是全面的。每当需要有关类的更多详细信息时，请参阅 [Dart API 参考资料](https://api.dart.dev/stable/2.7.1/index.html)

+ [dart:core](https://dart.dev/guides/libraries/library-tour#dartcore---numbers-collections-strings-and-more)

> 内置类型、集合和其他核心功能。此库自动导入到每个 Dart 程序中

+ [dart:async](https://dart.dev/guides/libraries/library-tour#dartasync---asynchronous-programming)

> 支持异步编程，包括 Future 和 Stream 等类

+ [dart:math](https://dart.dev/guides/libraries/library-tour#dartmath---math-and-random)

> 数学常数和函数，加上随机数发生器

+ [dart:convert](https://dart.dev/guides/libraries/library-tour#dartconvert---decoding-and-encoding-json-utf-8-and-more)

> 用于在不同数据表示形式（包括 JSON 和 UTF-8 ）之间转换的编码器和解码器

+ [dart:html](https://dart.dev/guides/libraries/library-tour#darthtml)

> 基于浏览器的应用程序的 DOM 和其他 API

+ [dart:io](https://dart.dev/guides/libraries/library-tour#dartio)

> 可使用 Dart 虚拟机的程序的 I/O，包括 Flutter 应用程序、服务器和命令行脚本

+ 此页只是一个概述；它只包含几个 dart:* 库，而没有第三方库

> 其他查找库信息的地方是 [pub.dev站点](https://pub.dev) 和 [Dart web developer库指南](https://dart.dev/web/libraries)。您可以在 [Dart API 参考资料](https://api.dart.dev/stable/2.7.1/index.html) 中找到所有 Dart 的 API 文档：*库，或者，如果您使用的是 [Flutter API 参考资料](https://api.flutter.dev)

## dart:core - numbers, collections, strings, and more

+ [dart:core 库](https://api.dart.dev/stable/2.7.1/dart-core/dart-core-library.html) 提供了一组小而关键的内置功能。此库自动导入到每个 Dart 程序中

+ 打印到控制台

> 顶级 print（）方法接受单个参数（任何对象）并在控制台中显示该对象的字符串值（由 toString（）返回）

```
print(anObject);
print('I drink $tea.');
```

+ Numbers

> dart:core 库定义了 num、int 和 double 类，这些类具有一些处理数字的基本实用程序
> 
> 可以分别使用 int 和 double 的 parse（）方法将字符串转换为整数或 double：

```
assert(int.parse('42') == 42);
assert(int.parse('0x42') == 66);
assert(double.parse('0.50') == 0.5);
```

> 或者使用 num 的 parse（）方法，如果可能的话创建一个整数，否则创建一个 double：

```
assert(num.parse('42') is int);
assert(num.parse('0x42') is int);
assert(num.parse('0.50') is double);
```

> 要指定整数的基数，请添加基数参数：

```
assert(int.parse('42', radix: 16) == 66);
```

> 使用 toString（）方法将 int 或 double 转换为字符串。要指定小数点右侧的位数，请使用 toStringAsFixed（）。要指定字符串中的有效位数，请使用 toStringsPrecision（）：

```
// Convert an int to a string.
assert(42.toString() == '42');

// Convert a double to a string.
assert(123.456.toString() == '123.456');

// Specify the number of digits after the decimal.
assert(123.456.toStringAsFixed(2) == '123.46');

// Specify the number of significant figures.
assert(123.456.toStringAsPrecision(2) == '1.2e+2');
assert(double.parse('1.2e+2') == 120.0);
```

+ 字符串和正则表达式

> Dart 中的字符串是不可变的 UTF-16 代码单元序列。可以使用正则表达式（ RegExp 对象）在字符串中搜索并替换字符串的部分。String 类定义了 split（）、contains（）、startsWith（）、endsWith（）等方法
> 
> *在字符串中搜索*
> 
> 您可以在字符串中找到特定的位置，并检查字符串是以特定模式开始还是以特定模式结束。例如：

```
// Check whether a string contains another string.
assert('Never odd or even'.contains('odd'));

// Does a string start with another string?
assert('Never odd or even'.startsWith('Never'));

// Does a string end with another string?
assert('Never odd or even'.endsWith('even'));

// Find the location of a string inside a string.
assert('Never odd or even'.indexOf('odd') == 6);
```

> *从字符串中提取数据*
> 
> 您可以从字符串中分别获取字符串或 int 形式的单个字符。准确地说，您实际上得到了单独的 UTF-16 代码单元；高编号字符（如高音谱号（'\u{1D11E}'）是每个代码单元的两个代码单元
> 
> 也可以提取子字符串或将字符串拆分为子字符串列表：

```
// Grab a substring.
assert('Never odd or even'.substring(6, 9) == 'odd');

// Split a string using a string pattern.
var parts = 'structured web apps'.split(' ');
assert(parts.length == 3);
assert(parts[0] == 'structured');

// Get a UTF-16 code unit (as a string) by index.
assert('Never odd or even'[0] == 'N');

// Use split() with an empty string parameter to get
// a list of all characters (as Strings); good for
// iterating.
for (var char in 'hello'.split('')) {
  print(char);
}

// Get all the UTF-16 code units in the string.
var codeUnitList =
    'Never odd or even'.codeUnits.toList();
assert(codeUnitList[0] == 78);
```

> *转换为大写或小写*
> 
> 您可以轻松地将字符串转换为其大小写变体：

```
// Convert to uppercase.
assert('structured web apps'.toUpperCase() ==
    'STRUCTURED WEB APPS');

// Convert to lowercase.
assert('STRUCTURED WEB APPS'.toLowerCase() ==
    'structured web apps');
```

> 注意：这些方法并不适用于所有语言。例如，土耳其字母的dotless I转换错误
> 
> *修剪和检查空字符串*
> 
> 使用 trim（）删除所有前导和尾随空白。要检查字符串是否为空（长度为零），请使用 isEmpty

```
// Trim a string.
assert('  hello  '.trim() == 'hello');

// Check whether a string is empty.
assert(''.isEmpty);

// Strings with only white space are not empty.
assert('  '.isNotEmpty);
```

> *替换字符串的一部分*
> 
> 字符串是不可变的对象，这意味着您可以创建它们，但不能更改它们。如果仔细查看字符串API引用，您会注意到没有一个方法实际更改了字符串的状态。例如，方法 replaceAll（）返回一个新字符串，而不更改原始字符串：

```
var greetingTemplate = 'Hello, NAME!';
var greeting =
    greetingTemplate.replaceAll(RegExp('NAME'), 'Bob');

// greetingTemplate didn't change.
assert(greeting != greetingTemplate);
```

> *建立一个字符串*
> 
> 要以编程方式生成字符串，可以使用 StringBuffer。在调用 toString（）之前，StringBuffer 不会生成新的字符串对象。writeAll（）方法有一个可选的第二个参数，用于指定分隔符（在本例中为空格）

```
var sb = StringBuffer();
sb
  ..write('Use a StringBuffer for ')
  ..writeAll(['efficient', 'string', 'creation'], ' ')
  ..write('.');

var fullString = sb.toString();

assert(fullString ==
    'Use a StringBuffer for efficient string creation.');
```

+ 正则表达式

> RegExp 类提供与 JavaScript 正则表达式相同的功能。使用正则表达式进行字符串的高效搜索和模式匹配

```
// Here's a regular expression for one or more digits.
var numbers = RegExp(r'\d+');

var allCharacters = 'llamas live fifteen to twenty years';
var someDigits = 'llamas live 15 to 20 years';

// contains() can use a regular expression.
assert(!allCharacters.contains(numbers));
assert(someDigits.contains(numbers));

// Replace every match with another string.
var exedOut = someDigits.replaceAll(numbers, 'XX');
assert(exedOut == 'llamas live XX to XX years');
```

> 您也可以直接使用 RegExp 类。Match 类提供对正则表达式匹配的访问

```
var numbers = RegExp(r'\d+');
var someDigits = 'llamas live 15 to 20 years';

// Check whether the reg exp has a match in a string.
assert(numbers.hasMatch(someDigits));

// Loop through all matches.
for (var match in numbers.allMatches(someDigits)) {
  print(match.group(0)); // 15, then 20
}
```

> *更多信息*
> 
> 
> [StringBuffer](https://api.dart.dev/stable/2.7.1/dart-core/StringBuffer-class.html)
> 
> [Pattern](https://api.dart.dev/stable/2.7.1/dart-core/Pattern-class.html)
> 
> [RegExp](https://api.dart.dev/stable/2.7.1/dart-core/RegExp-class.html)
> 
> [Match](https://api.dart.dev/stable/2.7.1/dart-core/Match-class.html)

+ Collections

> Dart 附带了一个核心集合 API，其中包括列表、集合和映射的类
> 
> *Lists*
> 
> 如语言教程所示，您可以使用字面量创建和初始化列表。或者，使用列表构造函数之一。List 类还定义了几种向列表中添加项和从列表中删除项的方法

```
// Use a List constructor.
var vegetables = List();

// Or simply use a list literal.
var fruits = ['apples', 'oranges'];

// Add to a list.
fruits.add('kiwis');

// Add multiple items to a list.
fruits.addAll(['grapes', 'bananas']);

// Get the list length.
assert(fruits.length == 5);

// Remove a single item.
var appleIndex = fruits.indexOf('apples');
fruits.removeAt(appleIndex);
assert(fruits.length == 4);

// Remove all elements from a list.
fruits.clear();
assert(fruits.isEmpty);
```

> 使用 index of（）查找列表中对象的索引

```
var fruits = ['apples', 'oranges'];

// Access a list item by index.
assert(fruits[0] == 'apples');

// Find an item in a list.
assert(fruits.indexOf('apples') == 0);
```

> 使用 Sort（）方法对列表排序。可以提供比较两个对象的排序函数。此排序函数必须返回 <0 表示较小，0 表示相同，>0 表示较大。下面的示例使用 compareTo（），compareTo 由Comparable 定义，并由 String 实现

```
var fruits = ['bananas', 'apples', 'oranges'];

// Sort a list.
fruits.sort((a, b) => a.compareTo(b));
assert(fruits[0] == 'apples');
```

> 列表是参数化类型，因此可以指定列表应包含的类型：

```
// This list should contain only strings.
var fruits = List<String>();

fruits.add('apples');
var fruit = fruits[0];
assert(fruit is String);
```

```
fruits.add(5); // Error: 'int' can't be assigned to 'String'
```

> 参考：[List API reference](https://api.dart.dev/stable/2.7.1/dart-core/List-class.html)
> 
> *Sets*
> 
> set 在 Dart 是一个唯一项目的无序集合。因为集合是无序的，所以不能按索引（位置）获取集合的项

```
var ingredients = Set();
ingredients.addAll(['gold', 'titanium', 'xenon']);
assert(ingredients.length == 3);

// Adding a duplicate item has no effect.
ingredients.add('gold');
assert(ingredients.length == 3);

// Remove an item from a set.
ingredients.remove('gold');
assert(ingredients.length == 2);
```

> 使用 contains（）和 containsAll（）检查一个或多个对象是否在一个 set 中：

```
var ingredients = Set();
ingredients.addAll(['gold', 'titanium', 'xenon']);

// Check whether an item is in the set.
assert(ingredients.contains('titanium'));

// Check whether all the items are in the set.
assert(ingredients.containsAll(['titanium', 'xenon']));
```

> 交集是其项在其他两个集合中的集合

```
var ingredients = Set();
ingredients.addAll(['gold', 'titanium', 'xenon']);

// Create the intersection of two sets.
var nobleGases = Set.from(['xenon', 'argon']);
var intersection = ingredients.intersection(nobleGases);
assert(intersection.length == 1);
assert(intersection.contains('xenon'));
```

> 参考：[Set API reference](https://api.dart.dev/stable/2.7.1/dart-core/Set-class.html)
> 
> *Maps*
> 
> 映射（通常称为字典或哈希）是键-值对的无序集合。映射将一个键与某个值相关联，以便于检索。与 JavaScript 不同，Dart 对象不是映射
> 
> 可以使用简洁的文字语法声明映射，也可以使用传统的构造函数：

```
// Maps often use strings as keys.
var hawaiianBeaches = {
  'Oahu': ['Waikiki', 'Kailua', 'Waimanalo'],
  'Big Island': ['Wailea Bay', 'Pololu Beach'],
  'Kauai': ['Hanalei', 'Poipu']
};

// Maps can be built from a constructor.
var searchTerms = Map();

// Maps are parameterized types; you can specify what
// types the key and value should be.
var nobleGases = Map<int, String>();
```

> 您可以使用括号语法添加、获取和设置映射项。使用remove（）从映射中移除键及其值

```
var nobleGases = {54: 'xenon'};

// Retrieve a value with a key.
assert(nobleGases[54] == 'xenon');

// Check whether a map contains a key.
assert(nobleGases.containsKey(54));

// Remove a key and its value.
nobleGases.remove(54);
assert(!nobleGases.containsKey(54));
```

> 可以从映射中检索所有值或所有键：

```
var hawaiianBeaches = {
  'Oahu': ['Waikiki', 'Kailua', 'Waimanalo'],
  'Big Island': ['Wailea Bay', 'Pololu Beach'],
  'Kauai': ['Hanalei', 'Poipu']
};

// Get all the keys as an unordered collection
// (an Iterable).
var keys = hawaiianBeaches.keys;

assert(keys.length == 3);
assert(Set.from(keys).contains('Oahu'));

// Get all the values as an unordered collection
// (an Iterable of Lists).
var values = hawaiianBeaches.values;
assert(values.length == 3);
assert(values.any((v) => v.contains('Waikiki')));
```

> 要检查映射是否包含键，请使用 containsKey（）。因为映射值可以为 null，所以不能仅仅依靠获取键的值并检查 null 来确定键的存在

```
var hawaiianBeaches = {
  'Oahu': ['Waikiki', 'Kailua', 'Waimanalo'],
  'Big Island': ['Wailea Bay', 'Pololu Beach'],
  'Kauai': ['Hanalei', 'Poipu']
};

assert(hawaiianBeaches.containsKey('Oahu'));
assert(!hawaiianBeaches.containsKey('Florida'));
```

> 如果且仅当键在映射中不存在时，要为键分配值，请使用 putIfAbsent（）方法。必须提供返回值的函数

```
var teamAssignments = {};
teamAssignments.putIfAbsent(
    'Catcher', () => pickToughestKid());
assert(teamAssignments['Catcher'] != null);
```

> 参考：[Map API reference](https://api.dart.dev/stable/2.7.1/dart-core/Map-class.html)
> 
> *常用的 collection 方法*
> 
> 列表、集合和映射共享许多集合中的常见功能。一些常见功能由 Iterable 类定义，该类列出并设置实现
> 
> 注意：虽然 Map 没有实现 Iterable，但是可以使用 Map keys 和 values 属性从中获取 Iterable
> 
> 使用 isEmpty 或 isNotEmpty 检查列表、集合或映射是否包含项：

```
var coffees = [];
var teas = ['green', 'black', 'chamomile', 'earl grey'];
assert(coffees.isEmpty);
assert(teas.isNotEmpty);
```

> 要将函数应用于列表、集或映射中的每个项，可以使用 forEach（）：

```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

teas.forEach((tea) => print('I drink $tea'));
```

> 在映射上调用 forEach（）时，函数必须有两个参数（键和值）：

```
hawaiianBeaches.forEach((k, v) {
  print('I want to visit $k and swim at $v');
  // I want to visit Oahu and swim at
  // [Waikiki, Kailua, Waimanalo], etc.
});
```

> Iterables 提供了 map（）方法，该方法为您提供单个对象中的所有结果：

```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

var loudTeas = teas.map((tea) => tea.toUpperCase());
loudTeas.forEach(print);
```

> 注意：map（）返回的对象是一个延迟计算的 Iterable：只有从返回的对象中请求一个项，才能调用函数
> 
> 要强制在每个项上立即调用函数，请使用map（）.toList（）或map（）.toSet（）：

```
var loudTeas =
    teas.map((tea) => tea.toUpperCase()).toList();
```

> 使用 Iterable 的 where（）方法获取与条件匹配的所有项。使用 Iterable 的 any（）和 every（）方法检查某些项或所有项是否与条件匹配

```
var teas = ['green', 'black', 'chamomile', 'earl grey'];

// Chamomile is not caffeinated.
bool isDecaffeinated(String teaName) =>
    teaName == 'chamomile';

// Use where() to find only the items that return true
// from the provided function.
var decaffeinatedTeas =
    teas.where((tea) => isDecaffeinated(tea));
// or teas.where(isDecaffeinated)

// Use any() to check whether at least one item in the
// collection satisfies a condition.
assert(teas.any(isDecaffeinated));

// Use every() to check whether all the items in a
// collection satisfy a condition.
assert(!teas.every(isDecaffeinated));
```

> 参考：[Iterable API reference](https://api.dart.dev/stable/2.7.1/dart-core/Iterable-class.html)

+ URIs

> Uri 类提供了在 Uri（您可能知道的 url）中使用的对字符串进行编码和解码的函数。这些函数处理特定于 uri 的字符，如 & 和 =。Uri 类还解析并公开 Uri 主机、端口、scheme 等的组件
> 
> *编码和解码完全限定的 URI*
> 
> 要对除 URI 中具有特殊含义的字符（如/、：、&、#）之外的字符进行编码和解码，请使用 encodeFull（）和 decodeFull（）方法。这些方法适合于对完全限定的 URI 进行编码或解码，保留完整的特殊 URI 字符

```
var uri = 'https://example.org/api?foo=some message';

var encoded = Uri.encodeFull(uri);
assert(encoded ==
    'https://example.org/api?foo=some%20message');

var decoded = Uri.decodeFull(encoded);
assert(uri == decoded);
```

> 注意，只有 some 和 message 之间的空间是如何编码的
> 
> *编码和解码URI组件*
> 
> 要对 URI 中具有特殊含义的字符串的所有字符（包括（但不限于）/、&、和：）进行编码和解码，请使用 encodeComponent（）和 decodeComponent（）方法

```
var uri = 'https://example.org/api?foo=some message';

var encoded = Uri.encodeComponent(uri);
assert(encoded ==
    'https%3A%2F%2Fexample.org%2Fapi%3Ffoo%3Dsome%20message');

var decoded = Uri.decodeComponent(encoded);
assert(uri == decoded);
```

> 注意每个特殊字符是如何编码的。例如， / 被编码为 %2F
> 
> *解析 URI*
> 
> 如果您有一个 Uri 对象或 Uri 字符串，则可以使用诸如 path 之类的 Uri 字段来获取其部分。要从字符串创建 Uri，请使用 parse（）静态方法：

```
var uri =
    Uri.parse('https://example.org:8080/foo/bar#frag');

assert(uri.scheme == 'https');
assert(uri.host == 'example.org');
assert(uri.path == '/foo/bar');
assert(uri.fragment == 'frag');
assert(uri.origin == 'https://example.org:8080');
```

> 参考：[ Uri API reference](https://api.dart.dev/stable/2.7.1/dart-core/Uri-class.html)
> 
> *构建 URI*
> 
> 可以使用 URI（）构造函数从各个部分构建 URI：

```
var uri = Uri(
    scheme: 'https',
    host: 'example.org',
    path: '/foo/bar',
    fragment: 'frag');
assert(
    uri.toString() == 'https://example.org/foo/bar#frag');
```

+ 日期和时间

> DateTime 对象是时间点。时区为 UTC 或本地时区
> 
> 可以使用多个构造函数创建 DateTime 对象：

```
// Get the current date and time.
var now = DateTime.now();

// Create a new DateTime with the local time zone.
var y2k = DateTime(2000); // January 1, 2000

// Specify the month and day.
y2k = DateTime(2000, 1, 2); // January 2, 2000

// Specify the date as a UTC time.
y2k = DateTime.utc(2000); // 1/1/2000, UTC

// Specify a date and time in ms since the Unix epoch.
y2k = DateTime.fromMillisecondsSinceEpoch(946684800000,
    isUtc: true);

// Parse an ISO 8601 date.
y2k = DateTime.parse('2000-01-01T00:00:00Z');
```

> 日期的 millisecondsSinceEpoch 属性返回自“Unix epoch”以来的毫秒数—1970年1月1日，UTC:

```
// 1/1/2000, UTC
var y2k = DateTime.utc(2000);
assert(y2k.millisecondsSinceEpoch == 946684800000);

// 1/1/1970, UTC
var unixEpoch = DateTime.utc(1970);
assert(unixEpoch.millisecondsSinceEpoch == 0);
```

> 使用 Duration 类计算两个日期之间的差异并向前或向后移动日期：

```
var y2k = DateTime.utc(2000);

// Add one year.
var y2001 = y2k.add(Duration(days: 366));
assert(y2001.year == 2001);

// Subtract 30 days.
var december2000 = y2001.subtract(Duration(days: 30));
assert(december2000.year == 2000);
assert(december2000.month == 12);

// Calculate the difference between two dates.
// Returns a Duration object.
var duration = y2001.difference(y2k);
assert(duration.inDays == 366); // y2k was a leap year.
```

> 警告：使用 Duration 按天移动日期时间可能会有问题，这是由于时钟移动（例如夏令时）。如果必须移动天数，请使用 UTC 日期
> 
> 参考：[DateTime](https://api.dart.dev/stable/2.7.1/dart-core/DateTime-class.html)  [Duration](https://api.dart.dev/stable/2.7.1/dart-core/Duration-class.html)

+ 实用工具类

> 核心库包含各种实用程序类，用于排序、映射值和迭代
> 
> *比较对象*
> 
> 实现 Comparable 接口以指示一个对象可以与另一个对象进行比较，通常用于排序。compareTo（）方法返回 <0 表示较小，0 表示相同，>0 表示较大

```
class Line implements Comparable<Line> {
  final int length;
  const Line(this.length);

  @override
  int compareTo(Line other) => length - other.length;
}

void main() {
  var short = const Line(1);
  var long = const Line(100);
  assert(short.compareTo(long) < 0);
}
```

> *实现映射键(map key)*
> 
> Dart 中的每个对象自动提供一个整数哈希代码，因此可以用作映射中的键。但是，可以重写 hashCode getter 以生成自定义哈希代码。如果您这样做了，您可能还需要重写 == 运算符。相等的对象（via==）必须具有相同的哈希代码。哈希代码不必是唯一的，但应该是分布良好的

```
class Person {
  final String firstName, lastName;

  Person(this.firstName, this.lastName);

  // Override hashCode using strategy from Effective Java,
  // Chapter 11.
  @override
  int get hashCode {
    int result = 17;
    result = 37 * result + firstName.hashCode;
    result = 37 * result + lastName.hashCode;
    return result;
  }

  // You should generally implement operator == if you
  // override hashCode.
  @override
  bool operator ==(dynamic other) {
    if (other is! Person) return false;
    Person person = other;
    return (person.firstName == firstName &&
        person.lastName == lastName);
  }
}

void main() {
  var p1 = Person('Bob', 'Smith');
  var p2 = Person('Bob', 'Smith');
  var p3 = 'not a person';
  assert(p1.hashCode == p2.hashCode);
  assert(p1 == p2);
  assert(p1 != p3);
}
```

> *迭代(Iteration)*
> 
> Iterable 和 Iterator 类支持 for-in 循环。只要创建一个类，该类可以提供迭代器供 for-in 循环使用，就可以扩展（如果可能）或实现 Iterable。实现迭代器来定义实际的迭代能力

```
class Process {
  // Represents a process...
}

class ProcessIterator implements Iterator<Process> {
  @override
  Process get current => ...
  @override
  bool moveNext() => ...
}

// A mythical class that lets you iterate through all
// processes. Extends a subclass of [Iterable].
class Processes extends IterableBase<Process> {
  @override
  final Iterator<Process> iterator = ProcessIterator();
}

void main() {
  // Iterable objects can be used with for-in.
  for (var process in Processes()) {
    // Do something with the process.
  }
}
```

+ 异常

> Dart 核心库定义了许多常见的异常和错误。异常被认为是可以提前计划并捕获的条件。错误是你不期望或不计划的情况
> 
> 最常见的错误有：
> 
> *NoSuchMethodError*
> 
> 当接收对象（可能为空）未实现方法时引发
> 
> *ArgumentError*
> 
> 可以由遇到意外参数的方法引发
> 
> 引发特定于应用程序的异常是指示发生错误的常见方法。可以通过实现异常接口定义自定义异常：

```
class FooException implements Exception {
  final String msg;

  const FooException([this.msg]);

  @override
  String toString() => msg ?? 'FooException';
}
```

## dart:async - asynchronous programming

+ 异步编程通常使用回调函数，但 Dart 提供了替代方法：Future 和 Stream 对象

> Future 就像是对未来某个时候所能提供的结果的承诺
> 
> Stream 是获取一系列值（如事件）的方法
> 
> Future、Stream 和更多都在 dart:async 库中
> 
> 注意：您并不总是需要直接使用 Future 或 Stream API。Dart 语言支持使用 async 和 await 等关键字进行异步编码
> 
> dart:async 库可以在 web 应用程序和命令行应用程序中工作。要使用它，请导入 dart:async：

```
import 'dart:async';
```

> 版本说明：从 Dart 2.1 开始，您不需要导入 Dart:async 来使用 Future 和 Stream  API，因为 Dart:core 导出这些类

+ Future

> Future 作为异步方法的返回对象，出现在整个 Dart 库中。future 完成之时就是数据可用之时
> 
> *使用 await*
> 
> 在直接使用 Future 的 API 之前，请考虑改用 await。使用 await 表达式的代码比使用 Future API 的代码更容易理解
> 
> 考虑下面的函数。它使用 Future 的 then（）方法连续执行三个异步函数，在执行下一个之前等待每个函数完成

```
runUsingFuture() {
  // ...
  findEntryPoint().then((entryPoint) {
    return runExecutable(entryPoint, args);
  }).then(flushThenExit);
}
```

> 等效的 await 表达式代码更像是同步代码：

```
runUsingAsyncAwait() async {
  // ...
  var entryPoint = await findEntryPoint();
  var exitCode = await runExecutable(entryPoint, args);
  await flushThenExit(exitCode);
}
```

> async 函数可以捕获 Future 的异常。例如：

```
var entryPoint = await findEntryPoint();
try {
  var exitCode = await runExecutable(entryPoint, args);
  await flushThenExit(exitCode);
} catch (e) {
  // Handle the error...
}
```

> 重要提示：async 函数返回 Future。如果不希望函数返回 Future，请使用其他解决方案。例如，可以从函数中调用 async 函数
> 
> *基本用法*
> 
> 可以使用 then（）来调度 Future 完成时运行的代码。例如，HttpRequest.getString（）返回 Future，因为 HTTP 请求可能需要一段时间。使用 then（）可以在 Future 完成且承诺的字符串值可用时运行一些代码：

```
HttpRequest.getString(url).then((String result) {
  print(result);
});
```

> 使用 catchError（）处理 Future 对象可能引发的任何错误或异常

```
HttpRequest.getString(url).then((String result) {
  print(result);
}).catchError((e) {
  // Handle or ignore the error.
});
```

> then（）.catchError（）模式是 try catch 的异步版本
> 
> 重要提示：请确保对 then（）的结果调用 catchError（）— 而不是对原始 Future 的结果。否则，catchError（）只能处理来自原始 Future 计算的错误，而不能处理由then（）注册的处理程序的错误
> 
> *链接多个异步方法*
> 
> then（）方法返回一个 Future，提供了按特定顺序运行多个异步函数的有用方法。如果使用then（）注册的回调返回一个 Future，then（）返回一个等价的 Future。如果回调返回任何其他类型的值，then（）将创建一个新的 Future，并用该值完成

```
Future result = costlyQuery(url);
result
    .then((value) => expensiveWork(value))
    .then((_) => lengthyComputation())
    .then((_) => print('Done!'))
    .catchError((exception) {
  /* Handle exception... */
});
```

> 在前面的示例中，方法按以下顺序运行：
> 
> 1.costlyQuery()
> 
> 2.expensiveWork()
> 
> 3.lengthyComputation()
> 
> 下面是使用 await 编写的相同代码：

```
try {
  final value = await costlyQuery(url);
  await expensiveWork(value);
  await lengthyComputation();
  print('Done!');
} catch (e) {
  /* Handle exception... */
}
```

> *等待多重 Future*
> 
> 有时，您的算法需要调用许多异步函数，并等待它们全部完成后再继续。使用 Future.wait（）静态方法管理多个 Future 并等待它们完成：

```
Future deleteLotsOfFiles() async =>  ...
Future copyLotsOfFiles() async =>  ...
Future checksumLotsOfOtherFiles() async =>  ...

await Future.wait([
  deleteLotsOfFiles(),
  copyLotsOfFiles(),
  checksumLotsOfOtherFiles(),
]);
print('Done with all the long steps!');
```

+ Stream

> Stream 对象出现在整个 Dart API 中，表示数据序列。例如，诸如按钮单击之类的 HTML 事件是使用 stream 传递的。也可以将文件作为 stream 读取
> 
> *使用异步 for 循环*
> 
> 有时您可以使用异步 for 循环（await for），而不是使用 stream API
> 
> 考虑下面的函数。它使用 Stream 的 listen（）方法订阅一个文件列表，传递一个搜索每个文件或目录的函数文本

```
void main(List<String> arguments) {
  // ...
  FileSystemEntity.isDirectory(searchPath).then((isDir) {
    if (isDir) {
      final startingDir = Directory(searchPath);
      startingDir
          .list(
              recursive: argResults[recursive],
              followLinks: argResults[followLinks])
          .listen((entity) {
        if (entity is File) {
          searchFile(entity, searchTerms);
        }
      });
    } else {
      searchFile(File(searchPath), searchTerms);
    }
  });
}
```

> 等效的 await 表达式代码，且包含异步 for 循环 (await for)如下（类似同步代码）：

```
Future main(List<String> arguments) async {
  // ...
  if (await FileSystemEntity.isDirectory(searchPath)) {
    final startingDir = Directory(searchPath);
    await for (var entity in startingDir.list(
        recursive: argResults[recursive],
        followLinks: argResults[followLinks])) {
      if (entity is File) {
        searchFile(entity, searchTerms);
      }
    }
  } else {
    searchFile(File(searchPath), searchTerms);
  }
}
```

> 重要提示：在使用 await for 之前，请确保它使代码更清晰，并且您确实希望等待 Stream 的所有结果。例如，您通常不应该对 DOM 事件监听器使用 await For，因为 DOM 发送无止境的事件流。如果使用 await for 在一行中注册两个 DOM 事件侦听器，则永远不会处理第二种事件
> 
> *监听流数据*
> 
> 要在到达时获取每个值，请使用 await for 或使用 listen（）方法订阅流：

```
// Find a button by ID and add an event handler.
querySelector('#submitInfo').onClick.listen((e) {
  // When the button is clicked, it runs this code.
  submitData();
});
```

> 在本例中，onClick 属性是由 submitInfo 按钮提供的流对象
> 
> 如果只关心一个事件，可以使用 first、last 或 single 等属性获取它。要在处理事件之前测试该事件，请使用诸如 firstWhere（）、lastWhere（）或 singleWhere（）等方法
> 
> 如果关心事件的子集，可以使用 skip（）、skipWhile（）、take（）、takeWhile（）和where（）等方法
> 
> *转换流数据*
> 
> 通常，在使用流数据之前，需要更改流数据的格式。使用 transform（）方法生成具有不同类型数据的流：

```
var lines = inputStream
    .transform(utf8.decoder)
    .transform(LineSplitter());
```

> 本例使用两个转换器。首先，它使用 utf8.decoder 将整数流转换为字符串流。然后它使用一个行拆分器将字符串流转换为单独的行流。这些转换器来自 dart:convert 库
> 
> *处理错误和完成*
> 
> 如何指定错误和完成处理代码取决于是使用异步 for 循环（await for）还是流API
> 
> 如果使用异步 for 循环，则使用 try catch 处理错误。流关闭后执行的代码在异步 for 循环之后执行

```
Future readFileAwaitFor() async {
  var config = File('config.txt');
  Stream<List<int>> inputStream = config.openRead();

  var lines = inputStream
      .transform(utf8.decoder)
      .transform(LineSplitter());
  try {
    await for (var line in lines) {
      print('Got ${line.length} characters from stream');
    }
    print('file is now closed');
  } catch (e) {
    print(e);
  }
}
```

> 如果使用流 API，则通过注册 onError 侦听器来处理错误。通过注册 onDone 侦听器在流关闭后运行代码

```
var config = File('config.txt');
Stream<List<int>> inputStream = config.openRead();

inputStream
    .transform(utf8.decoder)
    .transform(LineSplitter())
    .listen((String line) {
  print('Got ${line.length} characters from stream');
}, onDone: () {
  print('file is now closed');
}, onError: (e) {
  print(e);
});
```

## dart:math - math and random

+ dart:math 库提供了常见的功能，如正弦和余弦、最大值和最小值，以及常量，如 pi 和 e

> 数学库中的大多数功能都是作为顶级函数实现的
> 
> 若要在应用程序中使用此库，请导入 dart:math

```
import 'dart:math';
```

+ 三角函数

> Math 库提供基本的三角函数：

```
// Cosine
assert(cos(pi) == -1.0);

// Sine
var degrees = 30;
var radians = degrees * (pi / 180);
// radians is now 0.52359.
var sinOf30degrees = sin(radians);
// sin 30° = 0.5
assert((sinOf30degrees - 0.5).abs() < 0.01);
```

> 注意：这些函数使用弧度，而不是度数！

+ 最大值和最小值

> Math 库提供 max（）和 min（）方法：

```
assert(max(1, 1000) == 1000);
assert(min(1, -1000) == -1000);
```

+ 数学常数

> 在 Math 库中查找您最喜欢的常量 pi、e 等：

```
// See the Math library for additional constants.
print(e); // 2.718281828459045
print(pi); // 3.141592653589793
print(sqrt2); // 1.4142135623730951
```

+ 随机数

> 用 Random 类生成随机数。您可以选择为随机构造函数提供种子

```
var random = Random();
random.nextDouble(); // Between 0.0 and 1.0: [0, 1)
random.nextInt(10); // Between 0 and 9.
```

> 甚至可以生成随机布尔值：

```
var random = Random();
random.nextBool(); // true or false
```

## dart:convert - 解码和编码 JSON、UTF-8 等

+ dart:convert 库具有 JSON 和 UTF-8 的转换器，以及创建其他转换器的支持。JSON 是一种表示结构化对象和集合的简单文本格式。UTF-8 是一种常见的可变宽度编码，可以表示 Unicode 字符集中的每个字符

> dart:convert 库在web应用程序和命令行应用程序中都可以工作。要使用它，导入 dart:convert

```
import 'dart:convert';
```

+ 解码和编码 JSON

> 使用 jsonDecode（）将 JSON 编码的字符串解码为 Dart 对象：

```
// NOTE: Be sure to use double quotes ("),
// not single quotes ('), inside the JSON string.
// This string is JSON, not Dart.
var jsonString = '''
  [
    {"score": 40},
    {"score": 80}
  ]
''';

var scores = jsonDecode(jsonString);
assert(scores is List);

var firstScore = scores[0];
assert(firstScore is Map);
assert(firstScore['score'] == 40);
```

> 使用 jsonEncode（）将受支持的 Dart 对象编码为 JSON 格式的字符串：

```
var scores = [
  {'score': 40},
  {'score': 80},
  {'score': 100, 'overtime': true, 'special_guest': null}
];

var jsonText = jsonEncode(scores);
assert(jsonText ==
    '[{"score":40},{"score":80},'
        '{"score":100,"overtime":true,'
        '"special_guest":null}]');
```

> 只有 int、double、String、bool、null、List 或 Map（带字符串键）类型的对象可以直接编码为 JSON。List 和 Map 对象是递归编码的
> 
> 对于不能直接编码的对象，有两个编码选项。第一个是用第二个参数调用 encode（）：返回可直接编码的对象的函数。第二个选项是省略第二个参数，在这种情况下，编码器调用对象的toJson（）方法

+ UTF-8 字符的解码与编码

> 使用 utf8.decode（）将 utf8 编码的字节解码为 Dart 字符串：

```
List<int> utf8Bytes = [
  0xc3, 0x8e, 0xc3, 0xb1, 0xc5, 0xa3, 0xc3, 0xa9,
  0x72, 0xc3, 0xb1, 0xc3, 0xa5, 0xc5, 0xa3, 0xc3,
  0xae, 0xc3, 0xb6, 0xc3, 0xb1, 0xc3, 0xa5, 0xc4,
  0xbc, 0xc3, 0xae, 0xc5, 0xbe, 0xc3, 0xa5, 0xc5,
  0xa3, 0xc3, 0xae, 0xe1, 0xbb, 0x9d, 0xc3, 0xb1
];

var funnyWord = utf8.decode(utf8Bytes);

assert(funnyWord == 'Îñţérñåţîöñåļîžåţîờñ');
```

> 要将 UTF-8 字符流转换为 Dart 字符串，请将 utf8.decoder 指定为 stream transform（）方法：

```
var lines =
    utf8.decoder.bind(inputStream).transform(LineSplitter());
try {
  await for (var line in lines) {
    print('Got ${line.length} characters from stream');
  }
  print('file is now closed');
} catch (e) {
  print(e);
}
```

> 使用 utf8.encode（）将 Dart 字符串编码为 utf8 编码字节列表：

```
List<int> encoded = utf8.encode('Îñţérñåţîöñåļîžåţîờñ');

assert(encoded.length == utf8Bytes.length);
for (int i = 0; i < encoded.length; i++) {
  assert(encoded[i] == utf8Bytes[i]);
}
```

+ 其他功能

> dart:convert 库也有用于 ASCII 和 ISO-8859-1（Latin1） 的转换器

## dart:html ：基于浏览器的应用程序

+ 使用 dart:html 库对浏览器进行编程，操作 DOM 中的对象和元素，并访问 HTML5 API。DOM 代表文档对象模型，它描述 HTML 页面的层次结构

> dart:html 的其他常见用途包括操作样式（CSS）、使用 HTTP 请求获取数据以及使用 WebSockets 交换数据。HTML5（和 dart:html）有许多附加的 API，本节不涉及这些 API。只有 web 应用程序可以使用 dart:html，而不是命令行应用程序
> 
> 要在 web 应用程序中使用HTML库，请导入 dart:html：

```
import 'dart:html';
```

+ 操纵 DOM

> 要使用 DOM，您需要了解windows、文档(document)、元素(element)和节点(node)
> 
> Window 对象表示 web 浏览器的实际窗口。每个 Window 都有一个 Document 对象，该对象指向当前加载的文档。Window 对象还具有对各种 API 的访问器，如 IndexedDB（用于存储数据）、requestAnimationFrame（用于动画）等。在选项卡式浏览器中，每个选项卡都有自己的 Window 对象
> 
> 使用 Document 对象，可以在文档中创建和操作元素对象。请注意，Document 本身是一个元素，可以对其进行操作
> 
> DOM 为节点树建模。这些节点通常是元素，但也可以是属性、文本、注释和其他 DOM 类型。除了没有父节点的根节点之外，DOM 中的每个节点都有一个父节点，并且可能有许多子节点
> 
> *查找元素*
> 
> 要操作元素，首先需要一个表示它的对象。可以使用查询获取此对象
> 
> 使用顶级函数 querySelector（）和 querySelectorAll（）查找一个或多个元素。您可以按 ID、类、标记、名称或它们的任意组合进行查询。[CSS选择器规范指南](https://www.w3.org/TR/selectors-3/)定义选择器的格式，例如使用 # 前缀指定 id 和句点（.）指定类
> 
> querySelector() 函数的作用是：返回与选择器匹配的第一个元素，而querySelectorAll（）返回与选择器匹配的元素集合

```
// Find an element by id (an-id).
Element elem1 = querySelector('#an-id');

// Find an element by class (a-class).
Element elem2 = querySelector('.a-class');

// Find all elements by tag (<div>).
List<Element> elems1 = querySelectorAll('div');

// Find all text inputs.
List<Element> elems2 = querySelectorAll(
  'input[type="text"]',
);

// Find all elements with the CSS class 'class'
// inside of a <p> that is inside an element with
// the ID 'id'.
List<Element> elems3 = querySelectorAll('#id p.class');
```

> *操作元素*
> 
> 可以使用属性更改元素的状态。节点及其子类型元素定义所有元素都具有的属性。例如，所有元素都有 classes、hidden、id、style 和 title 属性，您可以使用这些属性来设置状态。元素的子类定义其他属性，例如 anchoreElement 的 href 属性
> 
> 考虑这个在 HTML 中指定 anchor 元素的例子：

```
<a id="example" href="/another/example">link text</a>
```

> 这个 <a> 标签指定一个具有一个 href 属性的元素和一个包含字符串 “linktext” 的文本节点（可通过 text 属性访问）。要更改链接指向的 URL，可以使用 AnchoreElement 的 href 属性：

```
var anchor = querySelector('#example') as AnchorElement;
anchor.href = 'https://dart.dev';
```

> 通常需要在多个元素上设置属性。例如，下面的代码设置类为“mac”、“win”或“linux”的所有元素的 hidden 属性。将 hidden 属性设置为 true 与向 CSS 添加 display:none 具有相同的效果

```
<!-- In HTML: -->
<p>
  <span class="linux">Words for Linux</span>
  <span class="macos">Words for Mac</span>
  <span class="windows">Words for Windows</span>
</p>
```

```
// In Dart:
final osList = ['macos', 'windows', 'linux'];
final userOs = determineUserOs();

// For each possible OS...
for (var os in osList) {
  // Matches user OS?
  bool shouldShow = (os == userOs);

  // Find all elements with class=os. For example, if
  // os == 'windows', call querySelectorAll('.windows')
  // to find all elements with the class "windows".
  // Note that '.$os' uses string interpolation.
  for (var elem in querySelectorAll('.$os')) {
    elem.hidden = !shouldShow; // Show or hide.
  }
}
```

> 当合适的属性不可用或不方便时，可以使用元素的 attributes 属性。此属性是 Map <String，String>，其中键是属性名。下面是设置属性值的示例：

```
elem.attributes['someAttribute'] = 'someValue';
```

> *创建元素*
> 
> 可以通过创建新元素并将它们附加到 DOM 来添加到现有的 HTML 页面。下面是创建段落（<p>）元素的示例：

```
var elem = ParagraphElement();
elem.text = 'Creating is easy!';
```

> 还可以通过解析HTML文本来创建元素。任何子元素也会被解析和创建

```
var elem2 = Element.html(
  '<p>Creating <em>is</em> easy!</p>',
);
```

> 注意 elem2 是上例中的 ParagraphElement
> 
> 通过为新创建的元素分配父元素，将其附加到文档。可以将元素添加到任何现有元素的子元素中。在下面的示例中，body 是一个元素，可以从 children 属性访问它的子元素（作为List<element>）

```
document.body.children.add(elem2);
```

> *添加、替换和删除节点*
> 
> 回想一下，元素只是一种节点。使用 Node 的 nodes 属性可以找到节点的所有子节点，该属性返回一个List<Node>（与忽略非元素节点的子节点不同）。拥有此列表后，可以使用常用的列表方法和运算符来操作节点的子节点
> 
> 要将节点添加为其父节点的最后一个子节点，请使用 List add（）方法：

```
querySelector('#inputs').nodes.add(elem);
```

> 要替换节点，请使用 Node replaceWith（）方法：

```
querySelector('#status').replaceWith(elem);
```

> 要删除节点，请使用 Node remove（）方法：

```
// Find a node by ID, and remove it from the DOM.
querySelector('#expendable').remove();
```

> *操作CSS样式*
> 
> CSS 或层叠样式表定义了 DOM 元素的表示样式。可以通过将ID和类属性附加到元素来更改元素的外观
> 
> 每个元素都有一个 classes 字段，它是一个列表。只需在此集合中添加和移除字符串，即可添加和移除CSS类。例如，以下示例将警告类添加到元素：

```
var elem = querySelector('#message');
elem.classes.add('warning');
```

> 按 ID 查找元素通常非常有效。可以使用 ID 属性动态设置元素 ID：

```
var message = DivElement();
message.id = 'message2';
message.text = 'Please subscribe to the Dart mailing list.';
```

> 通过使用方法级联，可以减少此示例中的冗余文本：

```
var message = DivElement()
  ..id = 'message2'
  ..text = 'Please subscribe to the Dart mailing list.';
```

> 虽然使用 ID 和 classes 将元素与一组样式关联是最佳实践，但有时您希望将特定样式直接附加到元素：

```
message.style
  ..fontWeight = 'bold'
  ..fontSize = '3em';
```

> *处理事件*
> 
> 要响应外部事件，如单击、焦点更改和选择，请添加事件侦听器。您可以将事件侦听器添加到页面上的任何元素。事件分派和传播是一个复杂的主题；如果您是web编程新手，请研究细节
> 
> 使用 element.onEvent.listen（function）添加事件处理程序，其中 event 是事件名，function 是事件处理程序
> 
> 例如，以下是如何处理单击按钮的操作：

```
// Find a button by ID and add an event handler.
querySelector('#submitInfo').onClick.listen((e) {
  // When the button is clicked, it runs this code.
  submitData();
});
```

> 事件可以通过 DOM 树上下传播。要发现最初触发事件的元素，请使用 e.target:

```
document.body.onClick.listen((e) {
  final clickedElem = e.target;
  // ...
});
```

> 要查看可以注册事件侦听器的所有事件，请在元素及其子类的 API 文档中查找“onEventType”属性。一些常见事件包括：
> 
> change
> 
> blur
> 
> keyDown
> 
> keyUp
> 
> mouseDown
> 
> mouseUp

+ 通过 HttpRequest 使用 HTTP 资源

> 以前称为 XMLHttpRequest，HttpRequest 类允许您从基于浏览器的应用程序中访问 HTTP 资源。传统上，AJAX 风格的应用程序大量使用 HttpRequest。使用 HttpRequest 从 web 服务器动态加载 JSON 数据或任何其他资源。您还可以动态地将数据发送到 web 服务器
> 
> *从服务器获取数据*
> 
> HttpRequest 静态方法 getString（）是从 web 服务器获取数据的简单方法。对 getString（）调用使用 await 以确保在继续执行之前拥有数据

```
Future main() async {
  String pageHtml = await HttpRequest.getString(url);
  // Do something with pageHtml...
}
```

> 使用 try-catch 指定错误处理程序：

```
try {
  var data = await HttpRequest.getString(jsonUri);
  // Process data...
} catch (e) {
  // Handle exception...
}
```

> 如果需要访问 HttpRequest，而不仅仅是它检索的文本数据，那么可以使用 request（）静态方法而不是 getString（）。下面是一个读取 XML 数据的示例：

```
Future main() async {
  HttpRequest req = await HttpRequest.request(
    url,
    method: 'HEAD',
  );
  if (req.status == 200) {
    // Successful URL access...
  }
  // ···
}
```

> 您还可以使用完整的 API 来处理更有趣的情况。例如，可以设置任意 header
> 
> 使用 HttpRequest 的完整 API 的一般流程如下：
> 
> 1.创建 HttpRequest 对象
> 
> 2.使用 GET 或 POST 打开 URL
> 
> 3.附加事件处理程序
> 
> 4.发送请求
> 
> 例如：

```
var request = HttpRequest();
request
  ..open('POST', url)
  ..onLoadEnd.listen((e) => requestComplete(request))
  ..send(encodedData);
```

> *向服务器发送数据*
> 
> HttpRequest 可以使用 HTTP 方法 POST 向服务器发送数据。例如，您可能希望将数据动态提交给表单处理程序。向 RESTful web 服务发送 JSON 数据是另一个常见的示例
> 
> 将数据提交到表单处理程序需要以 URI 编码字符串的形式提供名称-值对。如果要将数据发送到表单处理程序，还必须将内容类型头设置为 application/x-www-form-urlencode

```
String encodeMap(Map<String, String> data) => data.keys
    .map((k) => '${Uri.encodeComponent(k)}=${Uri.encodeComponent(data[k])}')
    .join('&');

Future main() async {
  var data = {'dart': 'fun', 'angular': 'productive'};

  var request = HttpRequest();
  request
    ..open('POST', url)
    ..setRequestHeader(
      'Content-type',
      'application/x-www-form-urlencoded',
    )
    ..send(encodeMap(data));

  await request.onLoadEnd.first;

  if (request.status == 200) {
    // Successful URL access...
  }
  // ···
}
```

+ 使用 WebSocket 发送、接收实时数据

> WebSocket 允许您的 web 应用与服务器交互地交换数据，无需轮询。服务器创建 WebSocket 并侦听以 ws:// - 例如，ws://127.0.0.1:1337/ws 开头的 URL 上的请求。通过 WebSocket 传输的数据可以是字符串或 blob。通常，数据是 JSON 格式的字符串
> 
> 要在 web 应用中使用 WebSocket，请首先创建 WebSocket 对象，并将 WebSocket URL 作为参数传递：

```
var ws = WebSocket('ws://echo.websocket.org');
```

> *发送数据*
> 
> 要在 WebSocket 上发送字符串数据，请使用 send（）方法：

```
ws.send('Hello from Dart!');
```

> 接收数据
> 
> 要在 WebSocket 上接收数据，请为消息事件注册侦听器：

```
ws.onMessage.listen((MessageEvent e) {
  print('Received message: ${e.data}');
});
```

> 消息事件处理程序接收消息事件对象。此对象的数据字段包含来自服务器的数据
> 
> *处理 WebSocket 事件*
> 
> 您的应用程序可以处理以下 WebSocket 事件：打开、关闭、错误和（如前所示）消息。下面是一个创建 WebSocket 对象并为打开、关闭、错误和消息事件注册处理程序的方法示例：

```
void initWebSocket([int retrySeconds = 1]) {
  var reconnectScheduled = false;

  print("Connecting to websocket");

  void scheduleReconnect() {
    if (!reconnectScheduled) {
      Timer(Duration(seconds: retrySeconds),
          () => initWebSocket(retrySeconds * 2));
    }
    reconnectScheduled = true;
  }

  ws.onOpen.listen((e) {
    print('Connected');
    ws.send('Hello from Dart!');
  });

  ws.onClose.listen((e) {
    print('Websocket closed, retrying in ' + '$retrySeconds seconds');
    scheduleReconnect();
  });

  ws.onError.listen((e) {
    print("Error connecting to ws");
    scheduleReconnect();
  });

  ws.onMessage.listen((MessageEvent e) {
    print('Received message: ${e.data}');
  });
}
```

## dart:io - 服务器和命令行应用程序的 I/O

+ dart:io 库提供了处理文件、目录、进程、套接字、WebSockets 以及 HTTP 客户端和服务器的 API

> 重要提示：只有 Flutter 移动应用程序、命令行脚本和服务器可以导入和使用 dart:io，而不是 web 应用程序
> 
> 通常，dart:io 库实现并提升异步 API。同步方法很容易阻塞应用程序，使其难以扩展。因此，大多数操作通过 Future 或 Stream 对象返回结果，这是 Node.js 等现代服务器平台常见的模式
> 
> dart:io 库中的少数同步方法在方法名上清楚地标记了 Sync 后缀。这里不包括同步方法
> 
> 要使用 dart:io 库，必须导入它：

```
import 'dart:io';
```

+ 文件和目录

> I/O 库允许命令行应用程序读写文件和浏览目录。您有两种读取文件内容的选择：一次全部读取或流式处理。同时读取一个文件需要足够的内存来存储文件的所有内容。如果文件非常大，或者您希望在读取时对其进行处理，则应使用流，如流文件内容中所述
> 
> *以文本形式读取文件*
> 
> 读取使用 UTF-8 编码的文本文件时，可以使用 readAsString（）读取整个文件内容。当单独的行很重要时，可以使用 readAsLines（）。在这两种情况下，都会返回一个 Future 对象，该对象将文件内容作为一个或多个字符串提供

```
Future main() async {
  var config = File('config.txt');
  var contents;

  // Put the whole file in a single string.
  contents = await config.readAsString();
  print('The file is ${contents.length} characters long.');

  // Put each line of the file into its own string.
  contents = await config.readAsLines();
  print('The file is ${contents.length} lines long.');
}
```

> *二进制方式读取文件*
> 
> 下面的代码将整个文件作为字节读入 int 列表。对 readAsBytes（）的调用返回一个 Future，该 Future 在可用时提供结果

```
Future main() async {
  var config = File('config.txt');

  var contents = await config.readAsBytes();
  print('The file is ${contents.length} bytes long.');
}
```

> *处理错误*
> 
> 要捕获错误以避免导致未捕获的异常，可以在将来注册 catchError 处理程序，或者（在异步函数中）使用 try-catch：

```
Future main() async {
  var config = File('config.txt');
  try {
    var contents = await config.readAsString();
    print(contents);
  } catch (e) {
    print(e);
  }
}
```

> *流文件内容*
> 
> 使用流读取文件，一次读取一点。您可以使用流 API 或 await for，这是 Dart 异步支持的一部分

```
import 'dart:io';
import 'dart:convert';

Future main() async {
  var config = File('config.txt');
  Stream<List<int>> inputStream = config.openRead();

  var lines =
      utf8.decoder.bind(inputStream).transform(LineSplitter());
  try {
    await for (var line in lines) {
      print('Got ${line.length} characters from stream');
    }
    print('file is now closed');
  } catch (e) {
    print(e);
  }
}
```

> *写入文件内容*
> 
> 可以使用 IOSink 将数据写入文件。使用 File openWrite（）方法获取可以写入的 IOSink。默认模式 FileMode.write 完全覆盖文件中的现有数据

```
var logFile = File('log.txt');
var sink = logFile.openWrite();
sink.write('FILE ACCESSED ${DateTime.now()}\n');
await sink.flush();
await sink.close();
```

> 要添加到文件末尾，请使用可选的 mode 参数指定 FileMode.append：

```
var sink = logFile.openWrite(mode: FileMode.append);
```

> 要写入二进制数据，请使用 add（List<int>data）
> 
> *在目录中列出文件*
> 
> 查找目录的所有文件和子目录是一个异步操作。list（）方法返回在遇到文件或目录时发出对象的流

```
Future main() async {
  var dir = Directory('tmp');

  try {
    var dirList = dir.list();
    await for (FileSystemEntity f in dirList) {
      if (f is File) {
        print('Found file ${f.path}');
      } else if (f is Directory) {
        print('Found dir ${f.path}');
      }
    }
  } catch (e) {
    print(e.toString());
  }
}
```

> *其他常见功能*
> 
> File 和 Directory 类包含其他功能，包括但不限于：
> 
> 创建文件或目录：File 和 Directory 的 create()
> 
> 删除文件或目录：File 和 Directory 的 delete()
> 
> 获取文件的长度：length（）in File
> 
> 获取对文件的随机访问：File 中的 open（）

+ HTTP 客户端和服务器

> dart:io 库提供了命令行应用程序可以用来访问 HTTP 资源以及运行 HTTP 服务器的类
> 
> *HTTP 服务器*
> 
> HttpServer 类提供了构建 web 服务器的低级功能。您可以匹配请求处理程序、设置头、流数据等
> 
> 下面的示例 web 服务器返回简单的文本信息。此服务器侦听端口 8888 和地址 127.0.0.1（本地主机），响应路径 /dart 的请求。对于任何其他路径，响应为状态代码404（找不到页面）

```
Future main() async {
  final requests = await HttpServer.bind('localhost', 8888);
  await for (var request in requests) {
    processRequest(request);
  }
}

void processRequest(HttpRequest request) {
  print('Got request for ${request.uri.path}');
  final response = request.response;
  if (request.uri.path == '/dart') {
    response
      ..headers.contentType = ContentType(
        'text',
        'plain',
      )
      ..write('Hello from the server');
  } else {
    response.statusCode = HttpStatus.notFound;
  }
  response.close();
}
```

> *HTTP 客户端*
> 
> HttpClient 类帮助您从 Dart 命令行或服务器端应用程序连接到 HTTP 资源。您可以设置头、使用 HTTP 方法以及读写数据。HttpClient 类在基于浏览器的应用程序中不起作用。在浏览器中编程时，请使用 dart:html HttpRequest 类。下面是使用 HttpClient 的示例：

```
Future main() async {
  var url = Uri.parse('http://localhost:8888/dart');
  var httpClient = HttpClient();
  var request = await httpClient.getUrl(url);
  var response = await request.close();
  var data = await utf8.decoder.bind(response).toList();
  print('Response ${response.statusCode}: $data');
  httpClient.close();
}
```

---
# [Intro to Dart for Java Developers codelab](https://codelabs.developers.google.com/codelabs/from-java-to-dart)

---
# [Effective Dart](https://dart.dev/guides/language/effective-dart)

+ 在过去的几年中，我们已经编写了大量的 Dart 代码，并了解了很多关于哪些代码工作良好，哪些不工作的信息。我们将与您共享这些信息，以便您也可以编写一致、健壮、快速的代码。有两大主题：

> *始终如一*
> 
> 当涉及到格式和大小写时，关于哪个更好的争论是主观的，不可能解决。我们所知道的是，保持一致在客观上是有帮助的
> 
> 如果两段代码看起来不同，那应该是因为它们在某种意义上是不同的。当一点代码突出并吸引了您的注意时，它应该这样做是因为一个有用的原因
> 
> *简短*
> 
> Dart 被设计得很熟悉，所以它继承了许多与 C、Java、JavaScript 和其他语言相同的语句和表达式。但我们创建 Dart 是因为在这些语言的基础上还有很大的改进空间。我们添加了一系列功能，从字符串插值到初始化表单，以帮助您更简单、更容易地表达您的意图
> 
> 如果有多种表达方式，你通常应该选择最简洁的一种。这并不是说你应该自己编写高尔夫代码，把整个程序塞进一行。目标是经济的代码，而不是密集的代码
> 
> Dart analyzer 有一个 linter 来帮助您编写良好的、一致的代码。如果存在可以帮助您遵循准则的 linter 规则，则准则链接到该规则。

## 指南

+ 为了便于消化，我们将指南分成了几页：

+ 款式指南

> 这定义了布局和组织代码的规则，或者至少定义了 dartfmt 不能为您处理的部分。样式指南还指定标识符的格式：camelCase、使用下划线等

+ 文档指南

> 这会告诉你所有你需要知道的关于注释的信息。文档注释和常规运行代码注释

+ 使用指南

> 这教你如何充分利用语言特性来实现行为。如果是在一个语句或表达式中，就在这里讨论

+ 设计指南

> 这是最软的指南，但却是范围最广的指南。它涵盖了我们在为库设计一致、可用的 API 方面所学到的知识。如果它在类型签名或声明中，则会忽略它

## 如何阅读指南

+ DO

> 指南描述了应始终遵循的实践。几乎永远不会有正当的理由离开他们

+ DON’T

> 指导方针是相反的：几乎从来不是好主意的事情。希望我们没有其他语言那么多，因为我们有更少的历史包袱

+ PREFER

> 准则是你应该遵循的实践。然而，在某些情况下，这样做是有意义的。当你这样做的时候，确保你理解忽略准则的全部含义

+ AVOID

> 准则是“偏好”的双重因素：你不应该做的事情，但在少数情况下可能有充分的理由去做

+ CONSIDER

> 指导原则是您可能希望或不希望遵循的实践，具体取决于环境、先例和您自己的偏好

+ 一些准则描述了规则不适用的例外情况。列出的例外情况可能并不详尽，您可能仍需要对其他情况作出判断

+ 听起来如果你的鞋带系不好，警察会打你的门。事情没那么糟。这里的指导原则大多是常识，我们都是通情达理的人。我们的目标，一如既往，是好的、可读的和可维护的代码

---
# [Asynchronous programming: futures, async, await](https://dart.dev/codelabs/async-await)

+ 这个 codelab 教你如何使用 futures 和 async 和 await 关键字编写异步代码。使用嵌入式 DartPad 编辑器，您可以通过运行示例代码和完成练习来测试您的知识

> 要充分利用这个 codelab，您应该具备以下条件：
> 
> 基本的 Dart 语法知识
> 
> 用另一种语言编写异步代码的一些经验
> 
> 该代码实验室包括以下材料：
> 
> 如何以及何时使用 async 和 await 关键字
> 
> 使用 async 和 await 如何影响执行顺序
> 
> 如何在异步函数中使用 try-catch 表达式处理异步调用中的错误

## 为什么异步代码很重要

+ 异步操作允许程序在等待另一个操作完成时完成工作。以下是一些常见的异步操作：

> 通过网络获取数据
> 
> 写入数据库
> 
> 从文件读取数据
> 
> 要在 Dart 中执行异步操作，可以使用 Future 类以及 async 和 await 关键字

+ 示例：错误地使用异步函数

> 下面的示例显示了使用异步函数（fetchUserOrder（））的错误方法。稍后您将使用 async 和 await 修复该示例。在运行此示例之前，请尝试找出问题所在—您认为输出将是什么？

```

```

> 下面是示例无法打印 fetchUserOrder（）最终生成的值的原因：
> 
> fetchUserOrder（）是一个异步函数，它在延迟之后提供一个描述用户顺序的字符串：“Large Latte”
> 
> 要获取用户的订单，createOrderMessage（）应该调用 fetchUserOrder（）并等待其完成。由于 createOrderMessage（）不等待fetchUserOrder（）完成， createOrderMessage（）无法获取 fetchUserOrder（）最终提供的字符串值
> 
> 相反，createOrderMessage（）获取待完成工作的表示：未完成的 future。你将在下一节学习更多关于 future 的知识
> 
> 由于 createOrderMessage（）无法获取描述用户订单的值，因此示例无法将“Large Latte”打印到控制台，而是打印“Your order is:Instance of''u Future'”
> 
> 在接下来的部分中，您将学习关于 futures、async 和 await，以便能够编写必要的代码，使 fetchUserOrder（）将所需的值（“Large Latte”）打印到控制台
> 
> *关键条款：*
> 
> 同步操作：同步操作阻止其他操作在完成之前执行
> 
> 同步函数：同步函数只执行同步操作
> 
> 异步操作：一旦启动，异步操作就允许在完成之前执行其他操作
> 
> 异步函数：异步函数至少执行一个异步操作，还可以执行同步操作

## 什么是 Future？

+ future（小写“f”）是 Future（大写“F”）类的实例。future表示异步操作的结果，可以有两种状态：未完成或已完成

> 注：Uncompleted 是一个 Dart 术语，指的是 Future 在产生价值之前的状态

+ Uncompleted

> 当调用异步函数时，它返回一个 Uncompleted Future。Future 正在等待函数的异步操作完成或引发错误

+ Completed

> 如果异步操作成功，则 Future 将使用一个值完成。否则它将以错误结束

+ Completing with a value

> Future <T> 类型的 Future 以 T 类型的值结束。例如，Future <String>类型的 Future 生成字符串值。如果 Future 不产生可用值，那么 Future 的类型是 Future <void>

+ Completing with an error

> 如果函数执行的异步操作由于任何原因而失败，则以后的操作将完成并出现错误


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
