## Java 的注释

单行注释：`//`，默认 IDEA 快捷键：`Ctrl + /`

多行注释：`/* */`，默认 IDEA 快捷键：`Ctrl + Shift + /`

文档注释：`/** */`，后面再学习

### 代码演示

```java
public class Hello {//类
    //这是主方法，作为Java程序的入口
    public static void main(String[] args) {//程序入口
        /*
        这是一个输出语句
        双引号的意思是把要输出的内容整合为一个字符串
         */
        System.out.println("atguigu");
//      快速进行单行注释的快捷键：Ctrl + /，再按一次取消这个注释
        System.out.println("hello");

        //多行注释的快捷键：Ctrl + Shift + /，再按一次取消这个注释
        System.out.println("1");
        System.out.println("2");
        System.out.println("3");
        System.out.println("4");
        //向下复制一行代码的快捷键：Ctrl + D

    }
}
```



## 关键字、保留字、特殊值

![image-20241126153446457](attachments/3_Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95.assets/image-20241126153446457.png)



## 标识符的命名规则和命名规范（记住它）

标识符：凡是程序中需要自己取名字的地方，都是标识符。

**命名规则：** 5 条，必须遵守，不遵守就报错

- 只用 26 个英文字母大小写、数字 `0-9`、美元符号 `$`、下划线 `_`
  - 理论上可以用中文来当标识符，但不推荐这么用，容易引起乱码等问题。
  - 因为 Java 采用万国码字符集 `Unicode` 字符集
- 不能数字开头
- 不能直接使用关键字、保留字、特殊值作为标识符
- 不能包含空格
- 严格区分大小写

**命名规范：** 建议遵守，不遵守不会报错，但是会被鄙视

- 见名知意
- 类名（`class` 后面）：必须遵循大驼峰命名法，形式：`XxxYyyZzz`，每一个单词首字母大写
- 变量名或方法名：必须遵循小驼峰命名法，形式：`xxxYyyZzz`，从第二个单词开始首字母大写。如果只有 1 个单词，就小写。
- 包名：全部小写，多个单词层级之间用 `.` 分割，形式：`xxx.yyy.zzz`
  - 习惯用公司域名倒置来取包名，例如：`com.atguigu.xxx`
- 常量名：全部大写，多个单词之间使用 `_` 分割，形式：`XXX_YYY_ZZZ`

## Java 的数据类型（先记基本数据类型 + `String`）

![image-20241126161609051](attachments/3_Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95.assets/image-20241126161609051.png)

> 高频面试题：
>
> `String` 是基本数据类型吗？不是，它是引用数据类型。



## 字面量值（掌握）

- `long`，数字后面加 `L`
- `float`，数字后面加 `F`
- `char`，用单引号，有且只有 1 个字符
- `boolean`：只能有 `true` 和 `false` 两个值
- `String`：不是基本数据类型，它用双引号，凡是程序中“”引起来都是字符串的值。

```java
public class TestLiteralValue {
    public static void main(String[] args) {
        //把光标定位到()里面，按Ctrl + P，会展示当前显示的是哪个类型
        //输出一个整数18
        System.out.println(18);//18默认是int类型
        System.out.println(18L);//18L明确是long类型
        //输出一个小数1.8
        System.out.println(1.8);//1.8默认是double类型
        System.out.println(1.8F);//1.8F明确是float，这里F大小写都可以

        //输出单个字符
        System.out.println('男'); //单引号
//        System.out.println('hi'); //错误，hi有2个字符，单引号里面只能有1个字符
      //  System.out.println('');//单引号里面有且只有1个字符

        //输出布尔值
        System.out.println(true);
        System.out.println(false);

        System.out.println("atguigu");//双引号，这个是字符串
        System.out.println("");//双引号里面可以空着，称为空字符串

        System.out.println("======================");
        System.out.println('a' + 'b');//可以算术运算符 + ,-,*,/等
        //'a'对应的编码值是97，'b'是98，所以结果是195
        System.out.println("a" + "b");//拼接
        /*
        + 只要没有字符串参与就是求和
        + 只有有字符串参与就是拼接
         */
    }
}

```

## 变量（掌握）

变量：它是用一个单词代表一个值，这个值可以修改。在程序中可以定义一些单词，称为变量名，用它们来代表一些数据。

**变量的声明：**

```java
数据类型 变量名;
```

**变量的赋值：**

```java
变量名 = 值;
```

**变量的使用有如下要求：**

- 变量必须先声明后使用
- 变量必须初始化
- 变量有作用域
- 同一个作用域中不能重复声明，但是可以反复赋值
- 给变量赋的值必须符合变量的类型

```java
public class TestVariable {
    public static void main(String[] args) {
        //存储一个年龄值
       // int age;//声明
      //  age = 18;//赋值

        //变量的第一次赋值称为初始化
        int age = 18;
        System.out.println(age);//只显示age变量里面的值 18
        System.out.println("age = " + age);//age = 18，这里"age = "是一个普通字符串，不是变量

        //快捷键
        // (1)变量名.sout
        System.out.println(age);
        //(2)变量名.soutv
        System.out.println("age = " + age);

        //变量的值可以修改
       age = 19;
        System.out.println(age);
    }

    //这是为了测试作用域的概念，随意写的另一个方法
    public static void test(){
//        System.out.println(age);//超出age的作用域
    }
}

```

### 案例

你用合适的变量，存储自己的个人信息：
姓名、年龄、性别、身高、体重、电话等
再输出显示

```java
public class MyInfo {
    public static void main(String[] args) {
        /*
        你用合适的变量，存储自己的个人信息：
        姓名、年龄、性别、身高、体重、电话等
        再输出显示

        String，System，MyInfo等都是类，遵循大驼峰命名法
         */
        String name = "柴林燕";
        int age = 18;
        char gender = '女';
        String sex = "美女";
        int height = 153;
        double weight = 45.2;
//        long tel = 1234567890;//一般不会用整数表示手机号码，身份证号码，银行卡号等
        String phone = "1234567890";//选中要修改的变量名，按快捷键Shift + F6，部分同学需要同时按Fn

        System.out.println("name = " + name);
        System.out.println("age = " + age);
        System.out.println("gender = " + gender);
        System.out.println("sex = " + sex);
        System.out.println("height = " + height);
        System.out.println("weight = " + weight);

        //修改同样的单词，但是它们不一定是变量，快捷键 Alt  + j，选中相同的单词，修改后按Esc
        System.out.println("phone = " + phone);
        System.out.println("phone = " + phone);
        System.out.println("phone = " + phone);
        System.out.println("phone = " + phone);
    }
}

```



## 拓展

随机产生 1 个整数

```java
import java.util.Random;
/*
Java中java.lang包下的类可以直接使用，不用导包，String,Math,System等
 */

public class RandomDemo {
    public static void main(String[] args) {
        //随机产生1个[0,1)范围小数
        //Math.random().var 等价于
        // Math.random()按快捷键 Ctrl  + Alt + V
        double num = Math.random();
        System.out.println("num = " + num);

        //随机产生1个[0,100)的整数
        /*
           0<=x<1
           0<=x*100<100
         */
        /*double a = Math.random() * 100;
        int b = (int) a;//强制转换
        System.out.println(a);
        System.out.println(b);*/

        Random rand = new Random();
        int b = rand.nextInt(0, 100);
        System.out.println("b = " + b);
    }
}
```



## 面试题

以下是为您提取的图片文字，您可以直接复制：

### 题 1：Java 的基本数据类型有哪些？

8 种基本数据类型：`byte`、`short`、`int`、`long`、`float`、`double`、`char`、`boolean`

特别说明：`String` 不属于基本数据类型

### 题 2：请简述标识符的命名规则和规范？

**命名规则：**

- 只能使用 26 个英文字母（大小写），数字 `0-9`，下划线 `_`，美元符号 `$`
- 数字不能开头
- 不能直接使用关键字、保留字、特殊值
- 不能包含空格
- 严格区分大小写

**命名规范：**

- 见名知意
- 类名：大驼峰命名法，形式：`XxxYyyZzz`
- 变量名：小驼峰命名法，形式：`xxxYyyZzz`
- 包名：所有单词小写，用 `.` 分割，形式：`xxx.yyy.zzz`
- 常量名：所有单词大写，用 `_` 分割，形式：`XXX_YYY_ZZZ`

以下是为您提取的图片文字，您可以直接复制：

### 题 3：Java 可以用中文当标识符吗？

可以，但是不会这么用

### 题 4：Java 的注释有几种？

- 单行注释：`//`
- 多行注释：`/* */`
- 文档注释：`/ */`

### 题 5：Java 的老东家和现东家是谁？

原来属于 SUN (Stanford University Network)，现在属于 Oracle (甲骨文)

### 题 6：JDK、JRE、JVM 是什么，有什么关系？

- **JDK**：Java 开发工具包 (Java Development Kit) (Java Developer's Kit)
- **JRE**：Java 运行环境 (Java Runtime Environment)
- **JVM**：Java 虚拟机 (Java Virtual Machine)
- `JDK = JRE + 开发工具`
- `JRE = JVM + 核心类库`
