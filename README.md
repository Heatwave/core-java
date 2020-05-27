# Java核心技术·卷 I - Fundamentals by Cay S. Horstmann

## 第一章 Java程序设计概述

## 第二章 Java程序设计环境

## 第三章 Java的基本程序设计结构

1. 一个简单的Java应用程序

    ```java
    public class FirstSample {
      public static void main(String[] args) {
        System.out.printLn(""Hello, World!"");
      }
    }
    ```

    1. Java区分大小写
    1. 类名必须以字母开头
        1. 后面可以跟字母和数字的任意组合
        1. 类名遵循大驼峰命名，CamelCase
1. 注释

    ```java
    /**
        这样的注释可以自动生成文档
     */
    ```

1. 数据类型
    1. 8 种基本类型
        1. 4 种整型
            1. int, short, long, byte
        1. 2 种浮点类型
            1. double, float
        1. 1 种表示 Unicode 编码的字符单元的字符类型 char
        1. boolean 类型
    1. 整型
        1. int 4字节
        1. short 2字节
        1. long 8字节
            1. 后缀 L 或 l
        1. byte 1字节
        1. 加上前缀0b或0B就可以写二进制数
            1. 例如0b1001 == 9
        1. 整型的范围与运行Java代码的机器无关
        1. 所有的数值类型所占据的字节数量与平台无关
        1. Java没有任何无符号(unsigned)类型
    1. 浮点类型
        1. float
            1. 4 字节
            1. 后缀F或f
        1. double
            1. 8字节
        1. 常量
            1. Double.POSITIVE_INFINITY
            1. Double.NEGATIVE_INFINITY
            1. Double.NaN
                1. if (x == Double.NaN) // is never true
                1. if (Double.isNan(x)) // check whether x is "not a number"
            1. Float.POSITIVE_INFINITY
            1. Float.NEGATIVE_INFINITY
            1. Float.NaN
    1. char类型
        1. char类型的字面量值要用单引号括起来
        1. 'A'是编码值为65所对应的字符常量，"A"是包含一个字符A的字符串
        1. 范围从\u0000到\Uffff
        1. 特殊字符的转义序列
            1. \b
            1. \t
            1. \n
            1. \r
            1. \"
            1. \'
            1. \\
        1. Unicode转义序列会在解析代码之前得到处理
            1. // \u00A0 is a newLine会产生语法错误，因为\u00A0会替换为一个换行符
    1. Unicode和char类型
        1. 强烈建议不要在程序中使用char类型，除非确实需要处理UTF-16代码单元。最好将字符串作为抽象数据类型处理。
    1. boolean类型
        1. true
        1. false
        1. 整型值和布尔值之间不能相互转换
1. 变量
    1. 不提倡在一行中声明多个变量，逐一声明每一个变量可以提高程序的可读性
    1. 变量初始化
        1. 变量的声明尽可能地靠近变量第一次使用的地方
    1. 常量
        1. final
            1. 常量名使用全大写，下划线分隔
    1. 类常量
        1. 在一个类的多个方法中使用的常量
        1. static final
            1. public static final double CM_PER_INCH_ = 2.54;
        1. 类常量的定义位于main方法的外部
        1. 如果一个常量被声明为public，那么其他类的方法也可以使用这个常量
1. 运算符
    1. 整数被0除将会产生一个异常，而浮点数被0除会得到无穷大或NaN结果
    1. 数学函数与常量
        1. 计算数值的平方根
            1. Math.sqrt(x)
        1. 幂运算
            1. Math.pow(x, a)
                1. 得到x的a次幂
                1. pow方法有两个double类型的参数，其返回结果也为double类型
        1. floorMod
        1. 三角函数
            1. Math.sinMath.cosMath.tanMath.atanMath.atan2
        1. 指数函数以及它的反函数——自然对数以及以10为底的对数
            1. Math.expMath.logMath.log10
        1. 表示PI和e常量的近似值
            1. Math.PIMath.E
    1. 静态导入
        1. import static java.lang.Math.*
            1. System.out.printLn("The square root of \u03c0 is " + sqrt(PI));
    1. 数值类型之间的转换
        1. 有精度损失的转换
            1. int -> float
            1. long -> double
            1. long -> float
    1. 强制类型转换(cast)
        1. int nx = (int) 9.997;
        1. 浮点舍入运算
            1. Math.round
        1. 不要在boolean类型与任何数值类型之间进行强制类型转换
    1. 结合赋值和运算符
        1. +=
    1. 自增与自减运算符
        1. 建议不要在表达式中使用++，因为这样的代码很容易让人困惑，而且会带来烦人的bug。
    1. 关系和boolean运算符
    1. 位运算符
        1. &
            1. and
        1. |
            1. or
        1. ^
            1. xor
        1. ~
            1. not
        1. \>>
            1. 右移，符号位填充高位
        1. <<
            1. 左移
        1. \>>>
            1. 右移，0填充高位
    1. 括号与运算符级别
    1. 枚举类型
        1. enum Size { SMALL, MEDIUM, LARGE, EXTRA_LARGE };
1. 字符串
    1. 每个用双引号括起来的字符串都是String类的一个实例
    1. 字串
        1. "Hello".substring(0, 3);
    1. 拼接
        1. \+
        1. 当将一个字符串与一个非字符串的值进行拼接时，后者被转换成字符串
        1. public static String join(CharSequence delimiter, CharSequence... elements)
    1. 不可变字符串
    1. 检测字符串是否相等
        1. s.equals(t)
        1. "Hello".equalsIgnoreCase("hello");
        1. 一定不要使用==运算符检测两个字符串是否相等
    1. 空串与Null串
        1. 检测字符串是否为空
            1. if (str.length() == 0)
            1. if (str.equals(""))
        1. 检测字符串是否为null
            1. if (str == null)
    1. 码点与代码单元
    1. String API
    1. 构建字符串

        ```java
        StringBuilder builder = new StringBuilder();
        builder.append(ch);
        builder.append(str);
        String completedString = builder.toString();
        ```

1. 输入输出
    1. 读取输入
        1. import java.util.*;
        1. Scanner in = new Scanner(System.in);
        1. String name = in.nextLine();
        1. String firstName = in.next();
            1. 读取一个单词，空白符作为分隔
        1. int age = in.nextInt();
    1. 格式化输出
    1. 文件输入与输出
        1. 读取文件
            1. Scanner in = new Scanner(Paths.get("myfile.txt", "UTF-8");
        1. 写入文件
            1. PrintWriter out = new PrintWriter("myfile.txt", "UTF-8");
1. 控制流程
    1. 块作用域
    1. 条件语句
        1. if ()
    1. 循环
        1. while ()
        1. do {} while ()
    1. 确定循环
        1. for
        1. for (double x = 0; x != 10; x += 0.1) ...
            1. 可能永远不会结束循环
    1. switch
        1. case 标签可以为
            1. char, byte, short, int
            1. enum
            1. 字符串字面量
    1. 中断控制流程语句
        1. break 可以带标签
        1. continue
1. 大数值
    1. BigInteger a = BigInteger.valueOf(100);
    1. BigInteger c = a.add(b);
    1. BigInteger d = c.multiply(b.add(BigInteger.valueOf(2)));
    1. BigDecimal
1. 数组
    1. int[] a = new int[100];
    1. int[] b = new int[n];
    1. 数字数组初始值为0
    1. boolean数组初始值为false
    1. 对象数组初始值为null
    1. for each 循环
        1. for (variable : collection) statement
        1. for (int element : a)  System.out.printLn(element);
    1. 数组初始化以及匿名数组
        1. int[] smallPrimses = {2, 3, 5, 7, 11, 13};
        1. new int[] {17, 19, 23, 29, 31, 37}
        1. smallPrimes = new int[] {17, 19, 23, 29, 31, 37};
    1. 数组拷贝
        1. int luckyNumbers = smallPrimes;
        1. 两个变量引用同一个数组
        1. int[] copiedLuckyNumbers = Arrays.copyOf(luckyNumbers, luckyNumbers.length);
    1. 命令行参数
        1. main方法的参数是一个字符串数组： String args[]
        1. java Message -g cruel world
            1. args[0]: "-g"
            1. args[1]: "cruel"
            1. args[2]: "world"
    1. 数组排序
        1. int[] a = new int[10000];......Arrays.sort(a);
            1. 使用了优化的快速排序算法
    1. java.util.Arrays
        1. static String toString(type[] a)
        1. static type copyOf(type[]a, int length)
        1. static type copyOfRange(type[] a, int start, int end)
        1. static void sort(type[] a)
        1. static int binarySearch(type[] a, type v)
            1. 二分搜索算法查找v
        1. static int binarySearch(type[] a, int start, int end, type v)
        1. static void fill(type[] a, type v)
        1. static boolean equals(type[] a, type[] b)
    1. 多维数组
    1. 不规则数组

## 第四章 对象与类

1. 面向对象程序设计概述
    1. 类
        1. 类 class
        1. 构造 construct
        1. 实例 instance
        1. 封装 encapsulation
        1. 实例域 instance field
        1. 方法 method
    1. 对象
        1. 对象的行为 behavior
        1. 对象的状态 state
        1. 对象标识 identity
    1. 识别类
        1. 识别类的简单规则是在分析问题的过程中寻找名词，而方法对应着动词
    1. 类之间的关系
        1. 依赖 uses-a
            1. 尽可能地将相互依赖的类减至最少
                1. 解耦
        1. 聚合 has-a
        1. 继承 is-a
1. 使用预定义类
    1. 对象与对象变量
        1. 构造新对象
            1. new Date()
            1. System.out.println(new Date())
            1. String s = new Date().toString()
            1. Date birthday = new Date()
        1. 可以显式地将对象变量设置为null， 表明这个对象变量目前没有引用任何对象
        1. 局部变量不会自动地初始化为null，而必须通过调用new或将它们设置为null进行初始化
    1. 标准库中的日期类
        1. 表示时间点的Date类
        1. 日历表示法的LocalDate类
            1. 不要使用构造器来构造LocalDate类的对象
            1. 应当使用静态工厂方法(factory method)调用构造器
            1. LocalDate.now()
            1. LocalDate.of(1999, 12, 31)
            1. getYear, getMonthValue, getDayOfMonth
        1. 更改器方法与访问器方法
        1. mutator method
        1. accessor method
1. 用户自定义类
    1. 多个源文件的使用
        1. javac Employee*.java
        1. javac EmployeeTest.java
            1. 自动查找需要编译的依赖文件
            1. 如果java文件较已有的class文件较新，自动重新编译文件
    1. 强烈建议将实例域标记为private
    1. 构造器
        1. 构造器与类同名
        1. 每个类可以有一个以上的构造器
        1. 构造器可以有0个、1个或多个参数
        1. 构造器没有返回值
        1. 构造器总是伴随着new操作一起调用
        1. 所有的Java对象都是在堆中构造的
        1. 不要在构造器中定义与实例域重名的局部变量
    1. 隐式参数与显式参数
        1. explicit
            1. 出现在方法声明中
        1. implicit
        1. 在每一个方法中，关键字this表示隐式参数
    1. 封装的优点
        1. 只返回实例域值的方法，称为域访问器
        1. 有些时候，需要获得或设置实例域的值，应该提供下面三项内容
            1. 一个私有的数据域
            1. 一个公有的域访问器方法
            1. 一个公有的域更改器方法
        1. 这样做有以下好处
            1. 改变内部实现时不影响其他代码
            1. 更改器方法可以执行错误检查
        1. 警告：注意不要编写返回引用可变对象的访问器方法
            1. 例如返回一个Date类，Date类有一个更改器方法setTime
            1. Date对象是可变的，这一点就破坏了封装性！
            1. 如果要返回一个可变对象的引用，应该首先对它进行克隆(clone)
    1. 基于类的访问权限
        1. 一个方法可以访问所属类的所有对象的私有属性
    1. 私有方法
        1. 有时，可能希望将一个计算代码划分成若干个独立的辅助方法。通常，这些辅助方法不应该成为公有接口的一部分，这是由于它们往往与当前的实现机制非常紧密，或者需要一个特别的协议以及一个特别的调用次序。最好将这样的方法设计为private的。
    1. final实例域
        1. 将实例域定义为final，构建对象时必须初始化这样的域，并且在后面的操作中，不能再对它进行修改。
        1. final修饰符大都应用于基本(primitive)类型域，或不可变(immutable)类的域
        1. 对可变的类使用final修饰符，只是表示该域的对象引用不会再变更为其他对象。但对象是可以更改的。
1. 4.4 静态域与静态方法
    1. 静态域
        1. static
            1. 类域
            1. 属于类，不属于任何独立的对象
    1. 静态常量
        1. public static final double PI = 3.14159265358979323846;
        1. 将域设置为公有时，最好将其设置为final
    1. 静态方法
        1. 是一种不能对对象实施操作的方法
            1. 换句话说，没有隐式的参数
            1. 没有this参数
        1. 使用类名调用静态方法
        1. 以下两种情况使用静态方法
            1. 一个方法不需要访问对象状态，其所需参数都是通过显式参数提供的（例如：Math.pow）
            1. 一个方法只需要访问类的静态域（例如：Employee.getNextId）
    1. 工厂方法
        1. 静态工厂方法(factory method)
        1. LocalDate.now
        1. LocalDate.of
        1. NumberFormat.getCurrencyInstance()
        1. NumberFormat.getPercentInstance()
    1. main方法
        1. 在启动程序时还没有任何一个对象。静态的main方法将执行并创建程序所需的对象

        ```java
        public class Application {
            public static void main(String[] args) {
                // construct objects here...
            }
        }
        ```

1. 4.5 方法参数
    1. 按值调用(call by value)
    1. 按引用调用(call by reference)
    1. Java总是采用按值调用，方法得到的是所有参数值的一个拷贝
    1. 方法不能修改传递给它的任何参数变量的内容
    1. 方法参数共有两种类型
        1. 基本数据类型(数字，布尔值)
        1. 对象引用
    1. 有些程序员认为Java对对象采用的是引用调用，实际上，这种理解是不对的
        1. 传递对象得到的是对象引用的拷贝
    1. Java中方法参数的使用情况：
        1. 一个方法不能修改一个基本数据类型的参数（即数值型或布尔型）
        1. 一个方法可以改变一个对象参数的状态
        1. 一个方法不能让对象参数引用一个新的对象
1. 4.6 对象构造
    1. 重载(overloading)
        1. 方法签名(signature)
            1. 方法名
            1. 参数类型
        1. 返回类型不是方法签名的一部分
    1. 默认域初始化
        1. 数值为0
        1. 布尔值为false
        1. 对象引用为null
        1. 如果不明确地对域进行初始化，就会影响程序代码的可读性
    1. 无参数的构造器
        1. 如果在编写一个类时没有编写构造器，系统会提供一个无参数构造器。这个构造器将所有的实例域设置为默认值。
        1. 如果类中提供了至少一个构造器，但是没有提供无参数的构造器。则在构造对象时如果没有提供参数就会被视为不合法。
    1. 显式域初始化
        1. 在类定义时给实例域设置一个有意义的初始值，是一种良好的设计习惯
    1. 参数名
        1. 构造器参数名使用和实例域相同的名字会将实例域屏蔽起来
        1. 使用单个字母的话不易理解
        1. 一些程序员在参数名前加'a'
        1. 或者使用this引用实例域
    1. 调用另一个构造器
        1. 如果构造器的第一个语句形如this(...)，这个构造器将调用同一个类的另一个构造器。
        1. 采用这种方法使用this关键字非常有用，这样对公共的构造器代码部分只编写一次即可。
    1. 初始化块
        1. 三种初始化数据域的方法
            1. 在构造器中设置值
            1. 在声明中赋值
            1. 初始化块(initialization block)
                1. 块语句放在域定义后，构造新对象时都会调用块内的语句
    1. 调用构造器的具体处理步骤
        1. 所有数据域被初始化为默认值(0, false 或 null)
        1. 按照在类声明中出现的次序，依次执行所有域初始化语句和初始化块
        1. 如果构造器第一行调用了第二个构造器，则执行第二个构造器主体
        1. 执行这个构造器的主体
    1. 静态域的初始化
        1. 提供一个初始化值
            1. private static int nextId = 1;
        1. 使用一个静态的初始化块

        ```java
        static {
            Random generator = new Random();
            nextId = generator.nextInt(10000);
        }
        ```

        1. 所有的静态初始化语句以及静态初始化块都将按照类定义的顺序执行
    1. 对象析构与finalize方法
        1. Java有自动的垃圾回收器，不支持析构器
        1. 如果某个资源需要在使用完毕后立刻被关闭，应该在对象用完时，调用一个close方法来完成相应的清理操作。
1. 4.7 包
    1. 从编译器的角度来看，嵌套的包之间没有任何关系。例如，java.util包与java.util.jar包毫无关系。每一个都拥有独立的类的集合
    1. 类的导入
        1. 访问另一个包中的共有类
            1. 第一种方式是在每个类名之前添加完整的包名
            1. 更简单且更常用的方式是使用import语句
        1. import语句应该位于源文件的顶部，但位于package语句的后面
            1. import java.util.*;
            1. import java.time.LocalDate;
        1. 增加一个特定的import语句解决命名冲突
            1. import java.util.*;import java.sql.*;import java.util.Date;
        1. 如果这两个Date都需要使用
            1. java.util.Date deadline = new java.util.Date();
            1. java.sql.Date today = new java.sql.Date(...);
        1. 在包中定位类是编译器(compiler)的工作。类文件中的字节码肯定使用完整的包名来引用其他类。
    1. 静态导入
        1. import static java.lang.System.*;
            1. out.printLn("Goodbye, World!");    // i.e. , System.outexit(0);    // i.e. , System.exit
        1. import static java.lang.System.out
    1. 将类放入包中
        1. 要想将一个类放入包中，就必须将包的名字放在源文件的开头，包中定义类的代码之前
        1. 如果没有在源文件中放置package语句，这个源文件中的类就被放置在一个默认包(default package)中。
    1. 编译器对文件(带有文件分隔符和扩展名.java的文件)进行操作而Java解释器加载类(带有.分隔符)
    1. 如果包与目录不匹配，虚拟机就找不到类
    1. 包作用域
        1. 如果没有指定public或private，这个部分(类、方法或变量)可以被同一个包中的所有方法访问
        1. 变量必须显式地标记为private，不然的话将默认为包可见
1. 4.8 类路径 (class path)
    1. 类的路径必须与包名匹配
    1. 类路径所列出的目录和归档文件是搜寻类的起始点
    1. . 表示当前目录
    1. 设置类路径
        1. java -classpath /home/user/classdir:.:/home/user/archives/archiv.jar MyProg
        1. export CLASSPATH=/home/user/classdir:.:/home/user/archives/archive.jar
        1. set CLASSPATH=c:\classdir;.;c:\archives\archive.jar
1. 4.9 文档注释
1. 4.10 类设计技巧
    1. 一定要保证数据私有
        1. 绝对不要破坏封装性
        1. 数据的表示形式很可能会改变，但它们的使用方式却不会经常发生变化
        1. 当数据保持私有时，它们的表示形式的变化不会对类的使用者产生影响
    1. 一定要对数据初始化
        1. 最好不要依赖于系统的默认值，而是应该显式地初始化所有的数据
        1. 具体的初始化方式可以是提供默认值，也可以是在所有构造器中设置默认值
    1. 不要在类中使用过多的基本类型
        1. 用其他的类代替多个相关的基本类型的使用
    1. 不是所有的域都需要独立的域访问器和域更改器
    1. 将职责过多的类进行分解
        1. 如果明显地可以将一个复杂的类分解成两个更为简单的类，就应该将其分解
    1. 类名和方法名要能够体现它们的职责
        1. 命名类名的良好习惯是采用一个名词(Order)、前面有形容词修饰的名词(RushOrder)或动名词(-ing)修饰名词(BillingAddress)
        1. 访问器方法用小写get开头，更改器方法用小写set开头
    1. 优先使用不可变的类
        1. 没有方法能够修改对象的状态
        1. 如果多个线程试图同时更新一个对象，就会发生并发更改。
        1. 如果类是不可变的，就可以安全地在多个线程间共享其对象。

## 第五章 继承

1. 5.1 类、超类和子类
    1. 定义子类
        1. public class Manger extends Employee{    ......}
    1. override
        1. 子类的方法不能够直接访问超类的私有域
        1. 可以通过super调用超类的公有方法
        1. 在子类中可以增加域、增加方法或覆盖超类的方法，然而绝对不能删除继承的任何域和方法
    1. 子类构造器
        1. 子类构造器里的super表示调用超类构造器
        1. 使用super调用构造器的语句必须是子类构造器的第一条语句
        1. 如果子类没有显式地调用超类构造器的话，则将自动地调用超类默认（没有参数）的构造器。
        1. 如果超类没有不带参数的构造器，并且子类的构造器中又没有显式调用超类的其他构造器，编译器将报错
    1. 一个对象变量可以指示多种实际类型的现象被称为多态(polymorphism)
    1. 在运行时能够自动地选择调用哪个方法的现象称为动态绑定(dynamic binding)
    1. 继承层次(inheritance hierarchy)
    1. 继承链(inheritance chain)
    1. 多态(polymorphism)
        1. "is-a"规则
        1. 表明子类的每个对象也是超类的对象
        1. 置换法则
        1. 表明程序中出现超类对象的任何地方都可以用子类对象置换
        1. 然而不能将一个超类的引用赋给子类变量
        1. 子类数组的引用可以转换成超类数组的引用，而不需要采用强制类型转换
        1. 所有数组都要牢记创建它们的元素类型，并负责监督仅将类型兼容的引用存储到数组中
    1. 理解方法调用
        1. 重载解析(overloading resolution)
        1. private方法、static方法、final方法或者构造器，调用方式为静态绑定(static binding)
        1. 其他方法在调用时依赖于隐式参数的实际类型，在运行时实现动态绑定
        1. 每次调用方法都要进行搜索，时间开销相当大，因此虚拟机预先为每个类创建了一个方法表(method table)。其中列出来所有方法的签名和实际调用的方法。
        1. 动态绑定有一个非常重要的特性：无需对现存的代码进行修改，就可以对程序进行扩展。
        1. 在覆盖一个方法时，子类方法不能低于超类方法的可见性。
    1. 阻止继承：final类和方法
        1. 不允许扩展的类被称为final类
            1. public final class Executive extends Manager {......}
        1. 类中的特定方法也可以被声明为final，这样子类就不能覆盖这个方法
            1. final类中的所有方法自动地成为final方法
        1. 将方法或类声明为final主要目的是：确保它们不会在子类中改变语义。
        1. 如果一个方法没有被覆盖并且很短，编译器就能够对它进行优化处理，这个过程称为内联(inlining)
        1. 虚拟机中的即时编译器可以准确地知道类之间的继承关系，并能够检测出类中是否真正地存在覆盖给定的方法
    1. 强制类型转换
        1. 进行类型转换的唯一原因是，在暂时忽视对象的实际类型之后，使用对象的全部功能。
        1. 将一个超类的引用赋给一个子类变量，必须进行类型转换，这样才能通过运行时检查。
        1. 如果试图将超类对象强制转换为子类对象，会产生一个ClassCastException异常。
        1. 在进行类型转换之前，使用instanceof操作符查看一下是否能成功地转换
            1. if (staff[1] instanceof Manager){    boss = (Manager) staff[1];    ......}
        1. 通过类型转换调整对象的类型并不是一种好的做法。
        1. 如果发现需要通过超类对象调用子类方法，那么就应该检查一下超类的设计是否合理，也许需要重新设计超类。
        1. 在一般情况下，应该尽量少用类型转换和instanceof运算符。
    1. 抽象类
        1. 包含一个或多个抽象方法的类本身必须被声明为抽象的
        1. 抽象方法
            1. public abstract String getDescription();
        1. 除了抽象方法外，抽象类还可以包含具体数据和具体方法
        1. 尽量将通用的域和方法(不管是否是抽象的)放在超类(不管是否是抽象类)中
        1. 抽象方法充当占位的角色，它们的具体实现在子类中。
        1. 扩展抽象类可以有两种选择
            1. 一种是在抽象类中定义部分抽象方法或不定义抽象类方法，这样就必须将子类也标记为抽象类
            1. 另一种是定义全部的抽象方法，这样一来，子类就不是抽象的了。
        1. 抽象类不能被实例化，也就是说，如果将一个类声明为abstract，就不能创建这个类的对象。
        1. 可以定义一个抽象类的对象变量，但是它只能引用非抽象子类的对象
        1. 编译器只允许调用在类中声明的方法
    1. 受保护访问
        1. 有时希望超类中的某些方法允许被子类访问，或允许子类的方法访问超类的某个域，为此，需要将这些方法或域声明为protected
        1. 谨慎使用protected属性，因为其他程序员可以由超类派生出新类，并访问其中的受保护域，如果需要修改超类的实现，就需要通知所有使用这个类的程序员，这违背了OOP提倡的数据封装原则。
        1. 如果需要限制某个方法的使用，就可以将它声明为protected，这表明子类(可能很熟悉祖先类)得到信任，可以正确地使用这个方法，而其他类则不行。
        1. 受保护的方法的一个最好的示例就是Object类中的clone方法
        1. 事实上，Java中的受保护部分对所有子类及同一个包中的所有其他类都可见。
    1. Java中用于控制可见性的4个访问修饰符
        1. 仅对本类可见： private
        1. 对所有类可见： public
        1. 对本包和所有子类可见：protected
        1. 对本包可见：默认，不需要修饰符
1. 5.2 Object：所有类的超类
    1. 如果没有明确地指出超类，Object就被认为是这个类的超类
    1. 可以使用Object类型的变量引用任何类型的对象
        1. 当然，Object类型的变量只能用于作为各种值的通用持有者。要想对其中的内容进行具体的操作，还需要清楚对象的原始类型，并进行相应的类型转换。
    1. 只有基本类型(primitive types)不是对象，例如数值、字符和布尔类型。
        1. 所有的数组类型，不管是对象数组还是基本类型的数组，都扩展了Object类。
    1. equals方法
        1. getClass方法将返回一个对象所属的类
        1. 在子类中定义equals方法时，首先调用超类的equals。
    1. 相等测试与继承
        1. Java语言规范要求equals方法具有下面的特性
            1. 自反性：对于任何非空引用x，x.equals(x)应该返回true。
            1. 对称性：对于任何引用x和y，当且仅当y.equals(x)返回true，x.equals(y)也应该返回true。
            1. 传递性：对于任何引用x、y和z，如果x.equals(y)返回true，y.equals(z)返回true，x.equals(z)也应该返回true。
            1. 一致性：如果x和y引用的对象没有发生变化，反复调用x.equals(y)应该返回相同的结果。
            1. 对于任意非空引用x，x.equals(null)应该返回false。
        1. 如果子类能够拥有自己的相等概念，则对称性需求将强制采用getClass进行检测。
        1. 如果由超类决定相等的概念，那么就可以使用instanceof进行检测，这样可以在不同子类的对象之间进行相等的比较。
        1. 编写一个完美的equals方法的建议
            1. 显式参数命名为otherObject，稍后需要将它转换成另一个叫做other的变量
            1. 检测this与otherObject是否引用同一个对象：if (this == otherObject) return true;
            1. 检测otherObject是否为null，如果为null，返回false：if (otherObject == null) return false;
            1. 比较this与otherObject是否属于同一个类，如果equals的语义在每个子类中有所改变，就使用getClass检测：if (getClass() != otherObject.getClass()) return false;
                1. 如果所有的子类都拥有统一的语义，就使用instanceof检测。
            1. 将otherObject转换为相应的类类型变量：ClassName other = (ClassName) otherObject
            1. 现在开始对所有需要比较的域进行比较。使用==比较基本类型域，使用equals比较对象域。如果所有的域都匹配，返回true，否则返回false。
        1. 对于数组类型的域，可以使用静态的Arrays.equals方法检测相应的数组元素是否相等。
        1. 为了避免发生类型错误，可以使用@Override对覆盖超类的方法进行标记：@Override public boolean equals(Object other)
            1. 注意覆盖的equals方法的签名要与超类Object的equals方法签名一致
        1. java.util.Arrays 1.2
            1. static boolean equals(type[] a, type[] b)
        1. java.util.Objects 7
            1. static boolean equals(Object a, Object b)
    1. hashCode方法
        1. 散列码是由对象导出的一个整形值，散列码是没有规律的，两个对象的散列码基本上不会相同
        1. 由于hashCode方法定义在Object类中，因此每个对象都有一个默认的散列码，其值为对象的存储地址。
        1. 如果重新定义equals方法，就必须重新定义hashCode方法，以便用户可以将对象插入到散列表中。
        1. hashCode方法应该返回一个整型数值（也可以是负数），并合理地组合实例域的散列码，以便能够让各个不同的对象产生的散列码更加均匀。
        1. 最好使用null安全的方法Objects.hashCode，如果其参数为null，这个方法会返回0，否则返回对参数调用hashCode的结果。
        1. 另外，使用静态方法Double.hashCode来避免创建Double对象
        1. Objects.hash可以用多个参数调用：Objects.(name, salary, hireDay)
        1. Equals与hashCode的定义必须一致，如果两个对象相等，那么它们的hash值也应该相等
        1. 可以使用静态的Arrays.hashCode方法计算整个数组的hash
    1. toString方法
        1. 绝大多数（但不是全部）的toString方法都遵循这样的格式：类的名字，随后是一对方括号括起来的域值。
        1. 最好通过调用getClass().getName()获得类名的字符串，而不要将类名硬加到toString方法中
        1. 如果超类使用了getClass().getName()，那么子类只要调用super.toString()就可以了
        1. 将数组转换为字符串需要使用静态方法Arrays.toString(...)
            1. 多维数组使用Arrays.deepToString
        1. 强烈建议为自定义的每一个类增加toString方法。这样做不仅自己受益，而且所有使用这个类的程序员也会从这个日志记录支持中受益匪浅。
1. 5.3 泛型数组列表
    1. ArrayList是一个采用类型参数(type parameter)的泛型类(generic class)
    1. ArrayList\<Employee> staff = new ArrayList\<Employee>();
    1. Java SE 7中：ArrayList\<Employee> staff = new ArrayList<>();
    1. 使用add方法可以将元素添加到数组列表中：
    1. staff.add(new Employee("Harry Hacker", ...));
    1. 如果已经清楚或能够估计出数组可能存储的元素数量，就可以在填充数组之前调用ensureCapacity方法：staff.ensureCapacity(100);
        1. 这个方法调用将分配一个包含100个对象的内部数组，然后调用100吃add，而不用重新分配空间
    1. 另外，还可以把初始容量传递给ArrayList构造器：
        1. ArrayList\<Employee> staff = new ArrayList<>(100);
    1. size方法将返回数组列表中包含的实际元素数目：
        1. staff.size()
    1. trimToSize方法将存储区域的大小调整为当前元素数量所需要的存储空间数目，垃圾回收期将回收多余的存储空间。
        1. 应该在确认不会添加任何元素时，再调用trimToSize
    1. 访问数组列表元素
        1. 使用get和set方法实现访问或改变数组元素的操作
            1. 设置第i个元素
                1. staff.set(i, harry);
                    1. set只能替换数组中已经存在的元素内容
            1. 获得第i个元素
                1. Employee e = staff.get(i);
        1. 使用toArray方法可以将数组元素拷贝到一个数组中
            1. X[] a = new X[list.size()];list.toArray(a);
        1. 带索引参数的add方法可以实现在数组列表中间插入元素
            1. staff.add(1, e);
        1. 从数组列表中间删除一个元素
            1. Employee e = staff.remove(n);
        1. 如果数组存储的元素数比较多，又经常需要在中间位置插入、删除元素，就应该考虑使用链表了。
        1. 可以使用for each循环遍历数组列表
            1. for (Employee e : staff) {}
    1. 类型化与原始数组列表的兼容性
1. 5.4 对象包装器与自动装箱
    1. 所有的基本类型都有一个与之对应的类 ，通常这些类称为包装器(wrapper)
        1. Integer
        1. Long
        1. Double
        1. Short
        1. Byte
        1. Character
        1. Void
        1. Boolean
        1. 前6个类派生于公共的超类Number
    1. 对象包装器是不可变的，即一旦构造了包装器，就不允许更改包装在其中的值。
        1. 对象包装器还是final，因此不能定义它们的子类
    1. 整形数组列表尖括号中的类型参数不允许是基本类型，不允许写成ArrayList\<int>
        1. 可以用Integer对象包装器类替代
        1. ArrayList\<integer> list = new ArrayList<>();
        1. 但是ArrayList\<Integer>的效率远远低于int[]
        1. 但是比int[]操作方便
    1. 自动装箱(autoboxing)
        1. list.add(3) 自动地变换成 list.add(Integer.valueOf(3));
    1. 自动拆箱
        1. int n = list.get(i); 变成 int n = list.get(i).intValue();
    1. 算术表达式中也能够自动地装箱和拆箱
    1. == 运算符也可以应用于对象包装器对象，只不过检测的是对象是否指向同一个存储区域。
        1. 两个包装器对象比较时应该调用equals方法
    1. 由于包装器类引用可以为null，所以自动装箱有可能会抛出一个NullPointerException异常
    1. 装箱和拆箱时编译器认可的，而不是虚拟机。编译器在生成类的字节码时，插入必要的方法调用。虚拟机只是执行这些字节码
    1. java.lang.Integer 1.0
        1. int intValue()
        1. static String toString(int i)
        1. static String toString(int i, int radix)
        1. static int parseInt(String s)
        1. static int parseInt(String s, int radix)
        1. static Integer valueOf(String s)
        1. static Integer valueOf(String s, int radix)
1. 5.5 参数数量可变的方法
    1. printf方法

        ```java
        public PrintStream printf(String format, Object ... args) {
            return format(format, args);
        }
        ```

    1. 省略号...是Java代码的一部分，它表明这个方法可以接收任意数量的对象（除fmt参数之外）
    1. 对于printf的实现者来说，Object...参数类型与Object[]完全一样
    1. 编译器需要对printf的每次调用进行转换，以便将参数绑定到数组上，并在必要的时候进行自动装箱
1. 5.6 枚举类
    1. public enum Size { SMALL, MEDIUM, LARGE, EXTRA_LARGE };
    1. 实际上，这个声明定义的类型是一个类，它刚好有4个实例。
    1. 在比较两个枚举类型的值时，永远不要调用equals，而直接使用==就可以了
    1. 如果需要的话，可以在枚举类型中添加一些构造器、方法和域。构造器只是在构造枚举常量的时候被调用。
    1. 所有的枚举类型都是Enum类的子类。
        1. toString方法能够返回枚举常量名，例如，Size.SMALL.toString()
            1. 返回字符串“SMALL”
        1. toString的逆方法时静态方法valueOf。例如：Size s = Enum.valueOf(Size.class, "SMALL");
            1. 将s设置成Size.SMALL
        1. 每个枚举类型都有一个静态的values方法，它将返回一个包含全部枚举值的数组。
        1. ordinal方法返回enum声明中枚举常量的位置，位置从0开始计数
1. 5.7 反射 reflective
    1. 能够分析类能力的程序称为反射。反射机制的功能及其强大，可以用来：
        1. 在运行时分析类的能力
        1. 在运行时查看对象，例如，编写一个toString方法供所有类使用
        1. 实现通用的数组操作代码
        1. 利用Method对象，这个对象很像C++中的函数指针
    1. Class类
        1. 在程序运行期间，Java运行时系统始终为所有的对象维护一个被称为运行时的类型标识，这个信息跟踪着每个对象所属的类。虚拟机利用运行时类型信息选择相应的方法执行。
        1. 可以通过专门的Java类访问这些信息。保存这些信息的类被称为Class，Object类中的getClass()方法将会返回一个Class类型的实例。
        1. 最常用的Class方法是getName，这个方法返回类的名字。
            1. 如果类在一个包里，包的名字也作为类名的一部分。
        1. 还可以调用静态方法Class.forName("java.util.Random")，获得类名对应的Class对象。
            1. 只有在className是类名或接口名时才能够执行，否则，forName方法将抛出一个checked exception（已检查异常），无论何时使用这个方法，都应该提供一个异常处理器（exception handler）
        1. 获得Class类对象的第三种方法非常简单，如果T时任意的Java类型（或void关键字），T.class将代表匹配的类对象。例如：Class cl1 = Random.class;
        1. 虚拟机为每个类型管理一个Class对象，因此，可以利用==运算符实现两个类型对象比较的操作：if (e.getClass()== Employee.class) ...
        1. newInstance()方法用来动态地创建一个类的实例。例如：e.getClass().newInstance()
            1. newInstance方法调用默认的构造器（没有参数的构造器）初始化新创建的对象，如果这个类没有默认的构造器，就会抛出一个异常。
        1. 将forName与newInstance配合起来使用，可以根据存储在字符串中的类名创建一个对象：
            1. String s = "java.util.Random";Object m = Class.forName(s).newInstance();
    1. 捕获异常
        1. 异常有两种类型：未检查异常和已检查异常。
            1. 对于已检查异常，编译器将会检查是否提供了处理器。
            1. 然而，有很多常见的异常，例如，访问null引用，都属于未检查异常。编译器不会查看是否为这些错误提供了处理器。
                1. 毕竟，应该精心编写代码来避免这些错误的发生，而不要将精力花在编写异常处理器上
    1. 利用反射分析类的能力
        1. 在java.lang.reflect包中有三个类Field，Method和Constructor分别用于描述类的域、方法和构造器。
            1. 这三个类都有一个叫做getName的方法，用来返回域、方法或构造器的名称。
        1. Field类有一个getType方法，用来返回描述域所属类型的Class对象。
        1. Method和Constructor类有能够报告参数类型的方法，Method类还有一个可以报告返回类型的方法。
        1. 这三个类还有一个叫做getModifiers的方法，它将返回一个整形数值，用不同的开关描述public和static这样的修饰符使用情况。
            1. 可以利用java.lang.reflect包中的Modifier类的静态方法分析getModifiers返回的整型数值
            1. 例如，使用Modifier类中的isPublic、isPrivate或isFinal判断方法或构造器是否是public、private或final。
            1. 还可以使用Modifier.toString方法将修饰符打印出来
        1. Class类中的getFields、getMethods和getConstructors方法将分别返回类提供的public域、方法和构造器数组，其中包括超类的公有成员。
        1. Class类的getDeclareFields、getDeclareMethods和getDeclaredConstructors方法将分别返回类中声明的全部域、方法和构造器，其中包括私有和受保护成员，但不包括超类的成员。
    1. 在运行时使用反射分析对象
        1. 前一节中，已经知道了如何查看任意对象的数据域名称和类型
            1. 获得对应的Class对象
            1. 通过Class对象调用getDeclaredFields
        1. 在编写程序时，如果知道想要查看的域名和类型，查看指定的域时一件很容易的事。而利用反射机制可以查看在编译时还不清楚的对象域。
        1. 如果f是一个Field类型的对象（例如，通过getDeclaredFields得到的对象），obj是某个包含f域的类的对象，f.get(obj)将返回一个对象，其值为obj域当前的值。
        1.  

        ```java
        Employee harry = new Employee("Harry Hacker", 35000, 10, 1, 1989);
        Class cl = harry.getClass();    // the class object representing Employee
        Field f = cl.getDeclaredField("name");    // the name field of the Employee class
        // 如果name是一个私有域，get方法将会抛出一个IllegalAccessException。
        Object v = f.get(harry);    // the value of the name field of the harry object, i.e. String object "Harry Hacker"
        ```

        1. 如果一个Java程序没有受到安全管理器的控制，就可以覆盖访问控制。
            1. 调用Field、Method或Constructor对象的setAccessible方法
            1. f.setAccessible(true);  // now OK to call f.get(harry)
        1. 如果想要查看的域是double类型，需要使用Field类中的getDouble方法，也可以调用get方法。反射机制将会自动地将这个域值打包到相应的对象包装器中。
        1. 调用f.set(obj, value)可以将obj对象的f域设置成新值。
    1. 使用反射编写泛型数组代码
        1. java.lang.reflect包中的Array类允许动态地创建数组。
        1. java.lang.reflect.Array类中的静态方法newInstance，能够构造新数组，在调用它时必须提供两个参数，一个是数组的元素类型，一个是数组的长度。
        1. Object newArray = Array.newInstance(componentType, newLength);
        1. 可以通过Array.getLength(a)或者Array类的静态getLength方法的返回值获得数组的长度
        1. 而要获得数组元素类型，需要：
            1. 首先获得a数组的类对象
            1. 确认它是一个数组
            1. 使用Class类（只能定义表示数组的类对象）的getComponentType方法确定数组对应的类型
        1. 扩展任意类型数组的反射方法：

            ```java
            public static goodCopyOf(Object a, int newLength) {
                Class cl = a.getClass();
                if (!cl.isArray())
                    return null;
                Class componentType = cl.getComponentType();
                int length = Array.getLength(a);
                Object newArray = Array.newInstance(componentType, newLength);
                System.arraycopy(a, 0, newArray, 0, Math.min(length, newLength));
                return newArray;
            }
            ```

            1. 应该将goodCopyOf的参数声明为Object类型，而不要声明为对象型数组（Object[]）。
            1. 整型数组类型int[]可以被转换成Object，但不能转换成对象数组。
    1. 调用任意方法
        1. 在C和C++中，可以从函数指针执行任意函数
        1. 表面上看，Java没有提供方法指针，既将一个方法的存储地址传给另一个方法，以便第二个方法能够随后调用它
        1. Java的设计者认为方法指针是很危险的，接口（interface）是一种更好的解决方案
        1. 然而，反射机制允许你调用任意方法。
        1. Method类中有一个invoke方法，它允许调用包装在当前Method对象中的方法。
        1. invoke方法的签名是
            1. Object invoke(Object obj, Object... args)
            1. 第一个参数是隐式参数，其余的对象提供了显式参数
            1. 对于静态方法，第一个参数可以被忽略，既可以将它设置为null
        1. 假设m1代表Employee类的getName方法，调用如下：
            1. String n = (String) m1.invoke(harry);
        1. 如果返回类型是基本类型，invoke方法会返回其包装器类型
            1. double s = (Double) m2.invoke(harry);
        1. 如何得到Method对象？
            1. 调用getDeclareMethods，对返回的Method对象数组进行查找
            1. 或调用Class类的getMethod方法得到想要的方法
        1. Method getMethod(String name, Class... parameterTypes)
        1. 可以使用Method对象实现C语言中函数指针的所有操作，但这种程序设计风格不太简便，出错的可能性也比较大。如果在调用方法的时候提供了一个错误的参数，那么invoke方法将会抛出一个异常。
        1. 另外，invoke的参数和返回值必须是Object类型的，这就意味着必须进行多次的类型转换。这样做将会使编译器错过检查代码的机会。
        1. 建议仅在必要的时候才使用Method对象，而最好使用接口以及lambda表达式。
        1. 建议Java开发者不要使用Method对象的回调功能。使用接口进行回调会使得代码的执行速度更快，更易于维护。
1. 5.8 继承的设计技巧
    1. 将公共操作和域放在超类
    1. 不要使用受保护的域
        1. protected机制并不能够带来更好的保护，原因有两点
            1. 第一，子类集合是无限制的，任何一个人都能够由某个类派生一个子类，并编写代码直接访问protected的实例域，从而破坏了封装性
            1. 第二，在Java中，同一个包中的所有类都可以访问protected域，而不管它是否为这个类的子类。
        1. protected方法对于指示那些不提供一般用途而应在子类中重新定义的方法很有用
    1. 使用继承实现“is-a”关系
        1. 如果类之间不是“is-a”关系，不要使用继承
    1. 除非所有继承的方法都有意义，否则不要使用继承
    1. 在覆盖方法时，不要改变预期的行为
        1. 置换法则不仅应用于语法，而且也应用于行为，这似乎更加重要。
        1. 在覆盖一个方法的时候，不应该毫无缘由地改变行为的内涵，编译器不会检查重新定义的方法是否有意义。
        1. 关键在于，在覆盖子类中的方法时，不要偏离最初的设计想法。
    1. 使用多态，而非类型信息
        1. if (x is of type 1)    action1(x);else if (x is of type 2)    action2(x);
            1. 如果action1与action2表示的是相同的概念，就应该为这个概念定义一个方法，并将其放置在两个类的超类或接口中，然后，就可以调用x.action();以便使用多态性提供的动态分派机制执行相应的动作。
    1. 不要过多的使用反射
        1. 反射对于编写系统程序来说极其实用，但是通常不适合于编写应用程序。
        1. 反射是很脆弱的，即编译器很难帮助人们发现程序中的错误，因此只有在运行时才发现错误并导致异常。

## 第六章 接口、lambda表达式与内部类

1. 6.1 接口
    1. 接口概念
        1. 接口不是类，而是对类的一组需求描述，这些类要遵从接口描述的统一格式进行定义。
        1. 例如，Arrays类中的sort方法承诺可以对对象数组进行排序，但要求满足下列前提：对象所属的类必须实现了Comparable接口。
        1. Comparable接口的代码：
            1. public interface Comparable\<T> { public int compareTo(T o); }
        1. 任何实现Comparable接口的类都需要包含compareTo方法，并且方法签名要与接口定义的方法相同
        1. 接口中的所有方法自动地属于public，因此，在接口中声明方法时，不必提供关键字public。
        1. 接口可以定义常量
            1. 但最好不要定义只有常量的接口
        1. 接口决不能含有实例域
        1. Java SE 8之前，不能在接口中实现方法
        1. 为了让类实现一个接口，通常需要下面两个步骤：
            1. 将类声明为实现给定的接口
                1. class Employee implements Comparable
            1. 对接口中的所有方法进行定义
        1. 在实现接口时，必须把方法声明为public
        1. API
            1. java.lang.Comparable\<T> 1.0
                1. int compareTo(T other)
            1. java.util.Arrays 1.2
                1. static void sort(Object[] a)
                1. mergesort: 归并排序
            1. java.lang.Integer 1.0
                1. static int compare(int x, int y) 7
            1. java.lang.Double 1.0
                1. static int compare(double x, double y) 1.4
    1. 接口的特性
        1. 不能使用new运算符实例化一个接口，但能声明接口的变量，接口变量必须引用实现了接口的类对象。
        1. 可以使用instanceof检查一个对象是否实现了某个特定的接口
        1. 接口也可以被扩展
            1. public interface Powered extends Moveable {}
        1. 接口中的域将被自动设为public static final
        1. 尽管每个类只能拥有一个超类，但却可以实现多个接口。
            1. 使用逗号将实现的各个接口分隔开
                1. class Employee implements Cloneable, Comparable
    1. 接口与抽象类
        1. 有些程序设计语言允许一个类有多个超类，例如C++。这样的特性叫做多继承（multiple inheritance）
        1. Java的设计者选择了不支持多继承，其主要原因是多继承会让语言本身变得非常复杂（如同C++），效率也会降低（如同Eiffel）
        1. 实际上，接口可以提供多重继承的大多数好处，同时还能避免多重继承的复杂性和低效性。
    1. 静态方法
        1. Java SE 8中，允许在接口中增加静态方法，虽然是合法的，但是这有违于接口作为抽象规范的初衷。
        1. 通常的做法都是将静态方法放在伴随类中，在标准库中，你会看到成对出现的接口和实用工具类。如Collection/Collections或Path/Paths。
    1. 默认方法
        1. 可以为接口方法提供一个默认实现，必须用default修饰符标记这样一个方法

            ```java
            public interface Comparable<T> {
                default int compareTo(T other) {
                    return 0;
                }        // By default, all elements are the same
            }
            ```

        1. 标记为default的方法可以不提供实现
        1. 默认方法可以调用任何其他方法
        1. 默认方法的一个重要用法是“接口演化”（interface evolution）
        1. 为接口增加一个非默认方法不能保证“源代码兼容”（source compatible）
        1. 不过，假设不重新编译新的类，只是使用原先的一个包含这个类的JAR包，仍能正常加载。“二进制兼容”
        1. 不过，调用新的方法仍会报错
        1. 将新方法实现为一个默认方法就可以解决这两个问题。
            1. 既能正常编译
            1. 如果没有重新编译而直接加载这个类，调用新方法时将调用接口的默认方法
    1. 解决默认方法冲突
        1. “类优先”规则
1. 6.2 接口示例
    1. 接口与回调
        1. 在Java标准类库中的类采用的是面向对象方法，它将某个类的对象传递给定时器，然后，定时器调用这个对象的方法。
        1. 定时器需要知道调用哪一个方法，并要求传递的对象所属的类实现了java.awt.event包的ActionListener接口。
            1. public interface ActionListener{    void actionPerformed(ActionEvent event);}
        1. 当到达指定的时间间隔时，定时器就调用actionPerformed方法
        1. Timer构造器的第一个参数是发出通告的时间间隔，它的单位是毫秒。第二个参数是监听器对象。
        1. ActionListener listener = new TimePrinter();Timer t = new Timer(10000, listener);t.start();
        1. API
            1. javax.swing.JOptionPane 1.2
                1. public static void showMessageDialog(Component parentComponent, Object message)
            1. javax.swing.Timer 1.2
                1. public Timer(int delay, ActionListener listener)
                1. public void start()
                1. public void stop()
            1. java.awt.Toolkit 1.0
                1. public static synchronized Toolkit getDefaultToolkit()
                1. public abstract void beep()
    1. Comparator接口
        1. Arrays.sort方法还有第二个版本，有一个数组和一个比较器（comparator）作为参数，比较器是实现了Comparator接口的类的实例。
        1. 要按长度比较字符串，可以如下定义一个实现Comparator\<String>的类

            ```java
            class LengthComparator implements Comparator<String> {
                public int compare(String first, String second) {
                    return first.length() - second.length();
                }
            }
            ```

        1. 具体完成比较时，需要构造一个实例

            ```java
            Comparator<String> comp = new LengthComparator();
            if (comp.compare(words[i], words[j]) > 0) ...
            ```

        1. 要对一个数组排序，需要为Arrays.sort方法传入一个LengthComparator对象：

            ```java
            String[] friends = { "Peter", "Paul", "Mary" };
            Arrays.sort(friends, new LengthComparator());
            ```

    1. 对象克隆
        1. clone方法是Object的一个protected方法，这说明你的代码不能直接调用这个方法。
        1. Object对于要拷贝的对象一无所知，所以只能逐个域地进行拷贝，并且是“浅拷贝”
        1. 如果原对象和浅克隆对象共享的子对象是不可变的，那么这种共享就是安全的。不过，通常子对象都是可变的，必须重新定义clone方法来建立一个深拷贝，同时克隆所有子对象。
        1. 对于每一个类，需要确定：
            1. 默认的clone方法是否满足要求
            1. 是否可以在可变的子对象上调用clone来修补默认的clone方法
            1. 是否不该使用clone
        1. 实际上第3个选项是默认选项，如果选择第1或第2项，类必须：
            1. 实现Cloneable接口
            1. 重新定义clone方法，并指定public访问修饰符
        1. 如果在一个对象上调用clone，但这个对象的类并没有实现Cloneable接口，Object类的clone方法就会抛出一个CloneNotSupportedException。
        1. 所有数组类型都有一个public的clone方法，而不是protected。可以用这个方法建立一个新数组，包含原数组所有元素的副本。
1. 6.3 lambda表达式
    1. 为什么引入lambda表达式
        1. lambda表达式是一个可传递的代码块，可以在以后执行一次或多次。
    1. lambda表达式的语法
        1. lambda表达式就是一个代码块，以及必须传入代码的变量规范
            1. (String first, String second)    -> first.length() - second.length()
        1. 如果代码要完成的计算无法放在一个表达式中，就可以像写方法一样，把这些代码放在{}中，并包含显式的return语句。
        1. 即使lambda表达式没有参数，仍然要提供空括号，就像无参数方法一样。
            1. () ->{......}
        1. 如果可以推到出一个lambda表达式的参数类型，则可以忽略其类型
        1. 如果方法只有一个参数，而且这个参数的类型可以推导得出，那么甚至还可以省略小括号：
            1. ActionListener listener = event -> ......
        1. 无需指定lambda表达式的返回类型。lambda表达式的返回类型总是会由上下文推导得出。
        1. 如果一个lambda表达式只在某些分支返回一个值，而在另外一些分支不返回值，这是不合法的。
    1. 函数式接口
        1. 对于只有一个抽象方法的接口，需要这种接口的对象时，就可以提供一个lambda表达式。这种接口称为函数式接口（functional interface）
        1. 最好把lambda表达式看作时一个函数，而不是一个对象，另外要接受lambda表达式可以传递到函数式接口
        1. 在Java中，对lambda表达式所能做的也只是转换为函数式接口。不像其他语言可以声明函数类型的变量
    1. 方法引用
        1. Timer t = new Timer(1000, System.out::println);
        1. 表达式System.out::println是一个方法引用（method reference），它等价于lambda表达式x -> System.out.println(x)
        1. Arrays.sort(strings, String::compareToIgnoreCase)
        1. 要用::操作符分隔方法名域对象或类名。主要有3种情况：
            1. object::instanceMethod
            1. Class::staticMethod
            1. Class::instanceMethod
        1. 前两种情况，方法引用等价于提供方法参数的lambda表达式。
    1. 构造器引用
        1. Person::new

            ```java
            ArrayList<String> names = ...;
            Stream<Person> stream = names.stream().map(Person::new);
            List<Person> people = stream.collect(Collectors.toList());
            ```

            1. map方法会为各个列表元素调用Person(String)构造器，如果有多个Person构造器，编译器会选择有一个String参数的构造器，因为它从上下文推导出这是在对一个字符串调用构造器。
        1. int[]::new
            1. 有一个参数：即数组的长度
            1. 等价于lambda表达式
                1. x ->new int[x]
    1. 变量作用域
        1. lambda表达式有3个部分
            1. 1. 一个代码块
            1. 2. 参数
            1. 3. 自由变量的值，指非参数而且不在代码中定义的变量
        1. lambda表达式可以捕获外围作用域中变量的值
        1. 在lambda表达式中，只能引用不会改变的变量
            1. 如果在lambda表达式中改变变量，并发执行多个动作时就会不安全。
        1. lambda表达式中捕获的变量必须实际上是final变量(effectively final)
        1. lambda表达式的body与嵌套块有相同的作用域
        1. lambda表达式中的this是指创建这个lambda表达式的方法的this参数
    1. 处理lambda表达式
        1. 使用lambda表达式的重点是延迟执行(deferred execution)
        1. 希望延迟执行的原因有：
            1. 在一个单独的线程中运行代码
            1. 多次运行代码
            1. 在算法的适当位置运行代码
            1. 发生某种情况时执行代码
            1. 只在必要时才运行代码
        1. 假设你想要重复一个动作n次，将这个动作和重复次数传递到一个repeat方法
            1. repeat(10, () ->System.out.println("Hello, World!"));
        1. 要接受这个lambda表达式，需要选择（或者提供）一个函数式接口
        1. 在这里，我们可以使用Runnable接口：
            1. public static void repeat(int n, Runnable action){    for (int i = 0; i < n; i++) action.run();}
    1. 再谈Comparator
        1. Comparator接口包含很多方便的静态方法来创建比较器。这些方法可以用于lambda表达式或方法引用。
        1. 静态comparing方法取一个“键提取器”函数，它将类型T映射为一个可比较的类型（如String）。对要比较的对象应用这个函数，然后对返回的键完成比较。

        ```java
        Arrays.sort(people, Comparator.comparing(Person::getName());
        Arrays.sort(people, Comparator.comparing(Person::getLastName).thenComparing(Person::getFirstName));
        Arrays.sort(people, Comparator.comparing(Person::getName, (s, t) ->Integer.compare(s.length(), t.length())));
        Arrays.sort(people, Comparator.comparingInt(p -> p.getName().length()));
        Arrays.sort(people, Comparator.comparing(Person::getMiddleName, nullsFirst(naturalOrder())));
        ```

1. 6.4 内部类
    1. 使用内部类访问对象状态
    1. 内部类的特殊语法规则
    1. 内部类是否有用、必要和安全
    1. 局部内部类
    1. 由外部方法访问变量
    1. 匿名内部类
    1. 静态内部类
1. 6.5 代理

## 第七章 异常、断言和日志

1. 7.1 处理异常
    1. 异常分类
        1. 异常对象都是派生于Throwable类的一个实例
        1. Error类层次结构描述了Java运行时系统的内部错误和资源耗尽错误，应用程序不应该抛出这种类型的对象。
        1. 由于程序错误导致的异常属于RuntimeException
        1. 程序本身没有问题，由于像I/O错误这类问题导致的异常属于其他异常
        1. 如果出现RuntimeException异常，那么就一定是你的问题
        1. Java语言规范将派生于Error类或RuntimeException类的所有异常称为非受查(unchecked)异常，所有其他的异常称为受查(checked)异常
        1. 编译器将核查是否为所有的受查异常提供了异常处理器。
    1. 声明受查异常
        1. 方法应该在其首部声明所有可能抛出的异常。
        1. 在下面4种情况时应该抛出异常
            1. 调用一个抛出受查异常的方法，例如，FileInputStream构造器
            1. 程序运行过程中发现错误，并且利用throw语句抛出一个受查异常
            1. 程序出现错误，例如，a[-1] = 0会抛出一个ArrayIndexOutOfBoundsException这样的非受查异常
            1. Java虚拟机和运行时库出现的内部错误
        1. 对于那些可能被他人使用的Java方法，应该根据异常规范，在方法的首部声明这个方法可能抛出的异常
        1. 不需要声明Java的内部错误，即从Error继承的错误
        1. 也不应该声明从RuntimeException继承的那些非受查异常
    1. 如何抛出异常
        1. 对于一个已经存在的异常类
            1. 找到一个合适的异常类
            1. 创建这个类的一个对象
            1. 将对象抛出
        1. 在Java中，只能抛出Throwable子类的对象
    1. 创建异常类
        1. 定义一个派生于Exception的类，或者派生于Exception子类的类
        1. 定义的类应该包含两个构造器，一个是默认的构造器，另一个是带有详细描述信息的构造器
    1. java.lang.Throwable 1.0
        1. Throwable()
        1. Throwable(String message)
        1. String getMessage()
1. 7.2 捕获异常
    1. 捕获异常

        ```java
        try {
            code
        } catch (ExceptionType e) {
            handler for this type
        }
        ```

        1. 通常，应该捕获那些知道如何处理的异常，而将那些不知道怎样处理的异常继续传递。
        1. 如果想传递一个异常，就必须在方法的首部添加一个throws说明符，以便告知调用者这个方法可能会抛出异常。
        1. 如果编写一个覆盖超类的方法，而这个方法又没有抛出异常，那么这个方法就必须捕获方法代码中出现的每一个受查异常。
    1. 捕获多个异常
        1. 同一个catch字句中可以捕获多个异常类型。

            ```java
            try {}
            catch (FileNotFoundException | UnKnownHostException e) {}
            ```

            1. 只有当捕获的异常类型彼此之间不存在子类关系时才需要这个特性。
            1. 捕获多个异常时，异常变量隐含为final变量
    1. 再次抛出异常与异常链
        1. 在catch字句中可以抛出一个异常，这样做的目的是改变异常的类型。
        1. 可以有一种更好的处理方法

            ```java
            try {
                access the database
            } catch (SQLException e) {
                Throwable se = new ServletException("database error");
                se.initCause(e);
                throw se;
            }
            ```

        1. 可以使用下面这条语句重新得到原始异常：
            1. Throwable e = se.getCause();
    1. finally字句
        1. 不管是否有异常被捕获，finally字句中的代码都被执行
        1. try语句可以只有finally字句，而没有catch子句
    1. 带资源的try语句
        1. try (Resource res = ...) { work with res }
        1. 假设资源属于一个实现了AutoCloseable接口的类，try块退出时，会自动调用res.close()
    1. 分析堆栈轨迹元素
        1. 可以调用Throwable类的printStackTrace方法访问堆栈轨迹的文本描述信息
        1. 一种更灵活的方法是使用getStackTrace方法，它会得到stackTraceElement对象的一个数组，可以在你的程序中分析这个对象数组
    1. java.lang.Throwable 1.0
        1. Throwable(Throwable cause)
        1. Throwable(String message, Throwable Cause)
        1. Throwable initCause(Throwable cause)
        1. Throwable getCause()
        1. StackTraceElement[] getStackTrace()
        1. void addSuppressed(Throwable t)
        1. Throwable[] getSuppressed()
    1. java.lang.Exception
        1. Exception(Throwable cause)
        1. Exception(String message, Throwable cause)
    1. java.lang.RuntimeException
        1. RuntimeException(Throwable cause)
        1. RuntimeException(String message, Throwable cause)
    1. java.lang.StackTraceElement
        1. String getFileName()
        1. int getLineNumber()
        1. String getClassName()
        1. String getMethodName()
        1. boolean isNativeMethod()
        1. String toString()
1. 7.3 使用异常机制的技巧
    1. 异常处理不能代替简单的测试
        1. 只在异常情况下使用异常机制
            1. 可以事先检查的就事先检查
    1. 不要过分地细化异常
        1. 将正常处理与错误处理分开
    1. 利用异常层次结构
        1. 不要只抛出RuntimeException异常。应该寻找更加适合的子类或创建自己的异常类
        1. 不要只捕获Throwable异常，否侧，会使程序更难读、更难维护
        1. 考虑受查异常与非受查异常的区别。已检查异常本来就很庞大，不要为逻辑错误抛出这些异常
        1. 将一种异常转换成另一种更加合适的异常时不要犹豫。
    1. 不要压制异常
    1. 在检测错误时，“苛刻”要比放任更好
    1. 不要羞于传递异常
    1. 早抛出，晚捕获
1. 7.4 使用断言
    1. 断言的概念
        1. 断言机制允许在测试期间向代码中插入一些检查语句。当代码发布时，这些插入的检测语言将会被自动地移走。
        1. assert 条件;
        1. assert 条件 : 表达式;
    1. 启用和禁用断言
        1. java -enableassertions MyApp
        1. java -ea MyApp
        1. java -ea:MyClass -ea:com.mycompany.mylib... MyApp
        1. java -ea:... -da:MyClass MyApp
    1. 使用断言完成参数检查
        1. Java中3种处理系统错误的机制:
            1. 抛出一个异常
            1. 日志
            1. 使用断言
        1. 什么时候应该使用断言？记住下面几点
            1. 断言失败是致命的、不可恢复的错误
            1. 断言检查只用于开发和测试阶段
        1. 不应该使用断言向程序的其他部分通告发生了可恢复性错误，或者，不应该作为程序向用户通告问题的手段
        1. 断言只应该用于在测试阶段确定程序内部的错误位置
        1. 计算机科学家将这种约定称为前置条件(Precondition)
    1. 为文档假设使用断言
1. 7.5 记录日志
    1. 基本日志
        1. Logger.getGlobal().info("File -> Open menu item selected");
        1. Logger.getGlobal().setLevel(Level.OFF);
    1. 高级日志
        1. 可以调用getLogger方法创建或获取记录器
            1. private static final Logger myLogger = Logger.getLogger("com.mycompany.myapp");
        1. 为了防止记录器被垃圾回收，要用一个静态变量存储日志记录器的一个引用。
        1. 如果对com.mycompany日志记录器设置了日志级别，它的子记录器也会继承这个级别
    1. 修改日志管理器配置
    1. 本地化
    1. 处理器
    1. 过滤器
    1. 格式化器
    1. 日志记录说明
1. 7.6 调试技巧
    1. 一个不太为人所知但却非常有效的技巧是在每一个类中放置一个单独的main方法。这样就可以对每一个类进行单元测试
    1. Junit
    1. 日志代理(logging proxy)
    1. printStackTrace
        1. Thread.dumpStack();
    1. Thread.setDefaultUncaughtExceptionHandler
    1. -verbose
    1. -Xlint
    1. jconsole
    1. jmap
        1. jhat
    1. -Xprof

## 第八章 泛型程序设计

1. 8.1 为什么要使用泛型程序设计
    1. 类型参数的好处
        1. 类型参数(type parameters)
        1. ArrayList\<String> files = new ArrayList\<String>();
        1. after Java SE7
            1. ArrayList\<String> files = new ArrayList<>();
        1. String filename = files.get(0);
        1. 使得程序具有更好的可读性和安全性
    1. 通配符类型(wildcard type)
1. 8.2 定义简单的泛型类
    1. 一个泛型类(generic class)就是具有一个或多个类型变量的类。

    ```java
    public class Pair<T> {
        private T first;
        private T second;
        ......
    }
    ```

    1. public class Pair<T, U> { ......}
    1. 类型变量使用大写形式，且比较短。
    1. 在Java库中，使用变量E表示集合的元素类型，K和V分别表示表的关键字与值的类型。T（或者U和S）表示任意类型
1. 8.3 泛型方法

    ```java
    class ArrayAlg {
        public static <T> T getMiddle(T... a) {
            return a[a.length / 2];
        }
    }
    ```

    1. String middle = ArrayAlg.getMiddle("John", "Q.", "Public");
    1. double middle = ArrayAlg.getMiddle(3.14, 1234.0, 0.0);
1. 8.4 类型变量的限定
    1. public static \<T extends Comparable> T min(T[] a) ......
    1. T extends Comparable &amp; Serializable
1. 8.5 泛型代码和虚拟机
    1. 类型擦除
        1. 泛型类型都有一个相应的原始类型（raw type）
        1. 原始类型的名字就是删去类型参数后的泛型类型名。擦除类型变量，并替换为限定类型（无限定的变量用Object）
        1. 原始类型用第一个限定的类型变量来替换，如果没有给定限定就用Object替换
    1. 翻译泛型表达式
        1. 当程序调用泛型方法时，如果擦除返回类型，编译器插入强制类型转换。
    1. 翻译泛型方法
        1. 用限定类型或Object替换类型参数
    1. 有关Java泛型转换的事实：
        1. 虚拟机中没有泛型，只有普通的类和方法
        1. 所有的类型参数都用他们的限定类型替换
        1. 桥方法被合成用来保持多态
        1. 为保持类型安全性，必要时插入强制类型转换
    1. 调用遗留的代码
1. 8.6 约束与局限性
    1. 不能用基本类型实例化类型参数
        1. 因为类型擦除之后，Object不能存储基本类型值
    1. 运行时类型查询只适用于原始类型
    1. 不能创建参数化类型的数组
    1. Varargs警告
    1. 不能实例化类型变量
    1. 不能构造泛型数组
    1. 泛型类的静态上下文中类型变量无效
    1. 不能抛出或捕获泛型类的实例
    1. 可以消除对受查异常的检查
    1. 注意擦除后的冲突
1. 8.7 泛型类型的继承规则
    1. Pair\<Manager>不是Pair\<Employee>的一个子类
1. 8.8 通配符类型
    1. 通配符概念
        1. Pair<? extends Employee>
            1. 表示任何泛型Pair类型，它的类型参数是Employee的子类，如Pair\<Manager>
        1. 类型Pair\<Manager>是Pair<? extends Employee>的子类型
    1. 通配符的超类型限定
        1. 超类型限定(supertype bound)
            1. ? super Manager
            1. 这个通配符限制为Manager的所有超类型
        1. 带有超类型限定的通配符可以向泛型对象写入，带有子类型限定的通配符可以从泛型对象获取。

        ```java
        public static <T extends Comparable<? super T>> T min(T[] a) ......
        ```

    1. 无限定通配符
    1. 通配符捕获
1. 8.9 反射和泛型
    1. 泛型Class类
    1. 使用Class\<T>参数进行类型匹配
    1. 虚拟机中的泛型类型信息

## 第九章 集合

1. 9.1 集合框架
    1. 将集合的接口与实现分离
        1. Java集合类库将接口与实现分离
        1. 队列(queue)
            1. 队列接口的最简形式

                ```java
                public interface Queue<E> {
                    void add(E element);
                    E remove();
                    int size();
                }
                ```

        1. 循环数组队列
            1. ArrayDeque
        1. 链表队列
            1. LinkedList
        1. 可以使用接口类型存放集合的引用
        1. 循环数组比链表高效，但循环数组是一个有界集合。如果程序中要收集的对象数量没有上限，就最好使用链表来实现。
    1. Collection接口
        1. 集合类的基本接口是Collection接口

            ```java
            public interface Collection<E> {
                boolean add(E element);
                Iterator<E> iterator();
                .......
            }
            ```

    1. 迭代器
        1. Iterator接口

            ```java
            public interface Iterator<E>{
                E next();
                boolean hasNext();
                void remove();
                default void forEachRemaining(Consumer<?super E> action);
            }
            ```

        1. for each循环可以与任何实现了Iterable接口的对象一起工作
        1. Collection接口扩展了Iterable接口，因此，对于标准类库中的任何集合都可以使用for each循环。
        1. 在Java SE 8中，可以调用forEachRemaining方法并提供一个lambda表达式（它会处理一个元素）。将对迭代器的每一个元素调用这个lambda表达式，直到再没有元素为止。
        1. 元素被访问的顺序取决于集合类型。如果对ArrayList进行迭代，迭代器将从索引0开始。如果访问HashSet中的元素，每个元素将会按照某种随机的次序出现。
        1. Java集合类库中的迭代器与其他类库中的迭代器在概念上有着重要的区别。
        1. 查找操作与位置变更是紧密相连的，查找一个元素的唯一方法时调用next，而在执行查找操作的同时，迭代器的位置随之向前移动
        1. 因此应该将Java迭代器认为是位于两个元素之间。当调用next时，迭代器就越过下一个元素，并返回刚刚越过的那个元素的引用。
        1. Iterator接口的remove方法将会删除上次调用next方法时返回的元素。
        1. 对next方法和remove方法的调用具有依懒性。
            1. 如果调用remove之前没有调用next将是不合法的。
    1. 泛型实用方法
        1. 由于Collection与Iterator都是泛型接口，可以编写操作任何集合类型的实用方法。

            ```java
            public static <E> boolean contains(Collection<E> c, Object obj) {
                for (E element : c)
                    if (element.equlas(obj))
                        return true;
                return false;
            }
            ```

    1. java.util.Collections\<E> 1.2
        1. Iterator\<E>iterator()
        1. int size()
        1. boolean isEmpty()
        1. boolean contains(Object obj)
        1. boolean containsAll(Collection<?> other)
        1. boolean add(Object element)
        1. boolean addAll(Collection<? extends E> other)
        1. boolean remove(Object obj)
        1. boolean removeAll(Collection<?> other)
        1. default boolean removeIf(Predicate<? super E>filter) 8
        1. void clear()
        1. boolean retainAll(Collection<?> other)
        1. Object[] toArray()
        1. \<T> T[] toArray(T[] arrayToFill)
    1. java.util.Iterator\<E> 1.2
        1. bolean hasNext()
        1. E next()
        1. void remove()
    1. 集合框架中的接口
1. 9.2 具体的集合
    1. 具体集合
        1. AbstractCollection
            1. AbstractList
                1. ArrayList
                    1. 一种可以动态增长和缩减的索引序列
                1. AbstractSequentialList
                    1. LinkedList
                        1. 一种可以在任何位置进行高效地插入和删除操作的有序序列
            1. AbstractSet
                1. HashSet
                    1. 一种没有重复元素的无序集合
                        1. LinkedHashSet
                            1. 一种可以记住元素插入次序的集合
            1. EnumSet
                1. 一种包含枚举类型值的集合
            1. TreeSet
                1. 一种有序集
        1. AbstractQueue
            1. PriorityQueue
                1. 一种允许高效删除最小元素的集合
        1. ArrayDeque
            1. 一种用循环数组实现的双端队列
        1. AbstractMap
            1. HashMap
                1. 一种存储键/值关联的数据结构
                    1. LinkedHashMap
                        1. 一种可以记住键/值项添加次序的映射表
            1. TreeMap
                1. 一种键值有序排列的映射表
            1. EnumMap
                1. 一种键值属于枚举类型的映射表
            1. WeakHashMap
                1. 一种其值无用武之地后可以被垃圾回收器回收的映射表
            1. IdentityHashMap
                1. 一种用==而不是用equals比较键值的映射表
    1. 除了以Map结尾的类之外都实现了Collection接口，以Map结尾的类实现了Map接口
    1. 链表
        1. LinkedList
            1. 双向链表

                ```java
                List<String> staff = new LinkedList<>();
                staff.add("Amy");
                staff.add("Bob");
                staff.add("Carl");
                Iterator iter = staff.iterator();
                String first = iter.next();
                String second = iter.next();
                iter.remove();
                ```

            1. 集合类库提供子接口ListIterator
                1. 其中的add方法不返回boolean类型的值，它假定添加操作总会改变链表。
                1. ListIterator接口有两个方法，可以用来反向遍历链表
                    1. E previous()
                    1. boolean hasPrevious()
                1. LinkedList类的listIterator方法返回一个实现了ListIterator接口的迭代器对象
                    1. ListIterator\<String> iter = staff.listIterator();
            1. add方法只依赖于迭代器的位置，而remove方法依赖于迭代器的状态
            1. set方法用一个新值取代调用next或previous方法返回的上一个元素
            1. 如果迭代器发现它的集合被另一个迭代器修改了，或是被该集合自身的方法修改了，就会抛出一个ConcurrentModificationException异常。
            1. 为了避免发生并发修改的异常，请遵循下述简单规则：
                1. 可以根据需要给容器附加许多的迭代器，但是这些迭代器只能读取列表。另外，再附加一个既能读又能写的迭代器。
            1. 链表只负责跟踪对列表的结构性修改
                1. set方法不被视为结构性修改。
            1. 链表不支持快速地随机访问，鉴于此，在程序需要采用整数索引访问元素时，通常不用链表
                1. LinkedList类还是提供了一个用来访问某个特定元素的get方法，这个方法的效率并不太高，如果发现自己正在使用这个方法，说明有可能对于所要解决的问题使用了错误的数据结构。
            1. 使用链表的唯一理由是尽可能地减少在列表中间插入或删除元素所付出的代价。
                1. 如果列表只有少数几个元素，就完全可以使用ArrayList
            1. 建议避免使用以整数索引表示链表中位置的所有方法
                1. 如果需要对集合进行随机访问，就使用数组或ArrayList，而不要使用链表。
            1. java.util.List\<E> 1.2
                1. ListIterator\<E> listIterator()
                1. ListIterator\<E> listIterator(int index)
                1. void add(int i, E element)
                1. void addAll(int i, Collection<? extends E> elements)
                1. E remove(int i)
                1. E get(int i)
                1. E set(int i, E element)
                1. int indexOf(Object element)
                1. int lastIndexOf(Object element)
            1. java.util.ListIterator\<E> 1.2
                1. void add(E newElement)
                1. void set(E newElement)
                1. boolean hasPrevious()
                1. E previous()
                1. int nextIndex()
                1. int previousIndex()
            1. java.util.LinkedList\<E> 1.2
                1. LinkedList()
                1. LinkedList(Collection<? extends E> elements)
                1. void addFirst(E element)
                1. void addLast(E element)
                1. E getFirst()
                1. E getLast()
                1. E removeFirst()
                1. E removeLast()
    1. 数组列表
        1. ArrayList
            1. 封装了一个动态再分配的对象数组
        1. Vector
            1. 动态数组
            1. 所有方法都是同步的，可以由两个线程安全地访问一个Vector对象
            1. 但是，如果由一个线程访问Vector，代码要在同步操作上耗费大量时间
        1. 不需要同步时使用ArrayList
1. 散列集
    1. 不在意元素的顺序
    1. 无法控制元素出现的次序
    1. 可以快速查找元素的数据结构
    1. 散列表为每个对象计算一个整数，称为散列码（hash code）
    1. 散列表用链表数组实现，每个列表被称为桶(bucket)
    1. 表中对象的位置是对象的散列码与桶的总数取余的结果
        1. 如对象散列码为76268，并且有128个桶，则对象应该保存在76268%128=108号bucket中
    1. hash collision
    1. rehashed
    1. load factor
    1. HashSet
        1. 只有不关心集合中元素的顺序时才应该使用HashSet
        1. 没有重复元素
    1. 散列集迭代器访问散列表元素的顺序是随机的
    1. 在更改集中的元素时要格外小心。如果元素的散列码发生了变化，元素在数据结构中的位置也会发生变化。
    1. java.util.HashSet\<E> 1.2
        1. HashSet()
        1. HashSet(Collection<? extends E> elements)
        1. HashSet(int initialCapacity)
        1. HashSet(int initialCapacity, float loadFactor)
    1. java.lang.Object 1.0
        1. int hashCode()
1. 树集
    1. TreeSet
    1. 是一个有序集合
    1. 插入后的元素会被放置在正确的排序位置上
        1. 排序是用树结构完成的（红黑树）
    1. 将一个元素添加到树中要比添加到散列表中慢
    1. 要使用TreeSet，必须能够比较元素。这些元素必须实现Comparable接口，或者构造set时必须提供一个Comparator
    1. 如果不需要对数据进行排序，就没有必要付出排序的开销。
    1. java.util.TreeSet\<E> 1.2
        1. TreeSet()
        1. TreeSet(Comparator<? super E> Comparator)
        1. TreeSet(Collection<? extends E> elements)
        1. TreeSet(SortedSet\<E> s)
    1. java.util.SortedSet\<E> 1.2
        1. Comparator<? super E> comparator()
        1. E first()
        1. E last()
    1. java.util.NavigableSet\<E> 6
        1. E higher(E value)
        1. E lower(E value)
        1. E ceiling(E value)
        1. E floor(E value)
        1. E pollFirst()
        1. E pollLast()
        1. Iterator\<E> descendingIterator()
1. 队列与双端队列
    1. 队列
        1. 可以有效地在尾部添加一个元素，在头部删除一个元素
    1. 双端队列
        1. 有效地在头部和尾部同时添加或删除元素
    1. 不支持在队列中间添加元素
    1. Deque接口，由ArrayDeque和LinkedList类实现，这两个类都提供了双端队列
    1. java.util.Queue\<E> 5.0
    1. java.util.Deque\<E> 6
    1. java.util.ArrayDeque\<E> 6
1. 优先级队列
    1. PriorityQueue
    1. remove方法总会获得当前优先级队列中最小的元素
    1. 使用堆(heap)作为数据结构
1. 9.3 映射
    1. 基本映射操作
        1. HashMap和TreeMap
            1. 都实现了Map接口
        1. 如果不需要按照排列顺序访问键，就最好选择HashMap
        1. getOrDefault
        1. put
        1. putAll
        1. containsKey
        1. forEach
        1. java.util.Map<K, V> 1.2
            1. V get(Object key)
            1. default V getOrDefault(Object key, V defaultValue)
            1. V put(K key, V value)
            1. void putAll(Map<? extends K, ? extends V> entries)
            1. boolean containsKey(Object key)
            1. boolean containsValue(Object value)
            1. default void forEach(BiConsumer<? super K, ? super V> action) 8
        1. java.util.HashMap<K, V> 1.2
        1. java.util.TreeMap<K, V> 1.2
        1. java.util.SortedMap<K, V> 1.2
    1. 更新映射项
        1. counts.put(word, counts.get(word) + 1);
        1. counts.put(word, counts.getOrDefault(word, 0) + 1);
        1. counts.putIfAbsent(word, 0);counts.put(word, counts.get(word) + 1);    // Now we know that get will succeed
        1. counts.merge(word, 1, Integer::sum);
    1. 映射视图
        1. java.util.Map<K, V> 1.2
            1. Set<Map.Entry<K, V>> entrySet()
            1. Set\<K> keySet()
            1. Collection\<V> values()
        1. java.util.Map.Entry<K, V> 1.2
            1. K getKey()
            1. V getValue()
            1. V setValue(V newValue)
    1. 弱散列映射
        1. WeakHashMap
    1. 链接散列集与映射
        1. LinkedHashSet
        1. LinkedHashMap
        1. 链接散列映射用访问顺序对映射条目进行迭代
        1. 每次调用get或put，受到影响的条目将从当前的位置删除，并放到条目链表的尾部
        1. 缓存
            1. 最近最少使用
    1. 枚举集与映射
        1. EnumSet
        1. EnumMap
    1. 标识散列映射
        1. IdentityHashMap
        1. java.lang.System 1.0
            1. static int identityHashCode(Object obj) 1.1
1. 9.4 视图与包装器
    1. 轻量级集合包装器
    1. 子范围
    1. 不可修改的视图
    1. 同步视图
    1. 受查视图
    1. 关于可选操作的说明
1. 9.5 算法
    1. 排序与混排
    1. 二分查找
    1. 简单算法
    1. 批操作
    1. 集合与数组的转换
    1. 编写自己的算法
1. 9.6 遗留的集合
    1. Hashtable类
    1. 枚举
    1. 属性映射
    1. 栈
    1. 位集

## 第十章 图形程序设计

## 第十一章 事件处理

## 第十二章 Swing用户界面组件

## 第十三章 部署Java应用程序

## 第十四章 并发
