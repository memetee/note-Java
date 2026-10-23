#  一、方法

## 1.1 方法的概念

在Java中方法用method表示，在其他语言中习惯叫函数（function）。

方法的定义：代表`一个`，`独立的`,`可复用的`，`功能`。

```
System.out.println(xx);  //println是一个方法，它完成打印xx到控制台，且换行。
Math.random();  //random()是一个方法，它完成了 随机产生1个[0,1)的double值给你。

Scanner input = new Scanner(System.in);
String str = input.next();  //next()是一个方法，它完成了 从控制台读取一个字符串的功能。
int num = input.nextInt();  //nextInt()是一个方法，它完成了 从控制台读取一个int值的功能。

public static void main(String[] args) 的main是一个方法，称为主方法，它作为Java程序的入口，由JVM自动调用。
```

## 1.2 方法的声明和调用

### 1.2.1 原则

- 方法必须先声明后使用
- 方法不调用不执行，调用一次执行一次

![image-20241204091205147](attachments/9_Java基础语法7.assets/image-20241204091205147.png)

![image-20241204091348158](attachments/9_Java基础语法7.assets/image-20241204091348158.png)

![image-20241204091447304](attachments/9_Java基础语法7.assets/image-20241204091447304.png)

### 1.2.2 方法的声明（必须掌握5个部分叫什么）

位置要求：方法必须定义/声明在类中，方法外

![image-20241204091633032](attachments/9_Java基础语法7.assets/image-20241204091633032.png)

声明的格式：

```
public class 类名{
    【①修饰符】 ②返回值类型  ③方法名(【④形参列表】){
        ⑤方法体语句;
    }
}

//【】表示可选
```

初期学习方法，方法由5个部分组成。

- 【①修饰符】：今天的方法暂时都是public static，public代表公共的，任意位置可见，static代表静态的，不需要new对象就可以调用这个方法。
- ②返回值类型：代表这个方法的功能执行完之后，是否需要给调用者返回一个结果。
- - 如果需要，就要说明这个结果的类型，它可以是8种基本数据类型或引用数据类型（Sstring类、数组等）。只要是非void，那么方法体中就必须有一个语句 return 结果; 否则代码编译不通过，报错。
  - 如果不需要，就用void表示。
- ③方法名：一个标识符而已。遵循小驼峰命名法，从第二个单词开始首字母大写。见名知意，即方法名能代表方法功能的意思。
- ⑤方法体语句：完成方法功能的语句。
- 【④形参列表】：它们其实就是一组变量，只不过这组变量的值需要在调用的时候由实参来赋值。如果这个方法完成功能的时候不需要额外的数据，那么形参列表可以省略。

![image-20241204092813279](attachments/9_Java基础语法7.assets/image-20241204092813279.png)

![image-20241204093034576](attachments/9_Java基础语法7.assets/image-20241204093034576.png)

### 1.2.3 演示

#### 1、无参无返回值

```
public class TestMethod5 {
    //功能：完成打印5行5列由*组成的矩形
    public static void print5Line5ColumnRectangle(){//无参无返回值
        for(int i=1; i<=5; i++){
            for(int j=1; j<=5; j++){
                System.out.print("*");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
//        System.out.println(print5Line5ColumnRectangle());//错误，因为print5Line5ColumnRectangle方法没有结果返回，不能打印结果
        print5Line5ColumnRectangle();
    }
}
```

![image-20241204093819676](attachments/9_Java基础语法7.assets/image-20241204093819676.png)

#### 2、有参无返回值

```
public class TestMethod6 {
    //功能：完成打印m行n列由某符号组成的矩形
    public static void printRectangle(int m, int n, char c){//有参无返回值
        for(int i=1; i<=m; i++){
            for(int j=1; j<=n; j++){
                System.out.print(c);
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        printRectangle(5,10, '@');
        System.out.println("=================================");
        printRectangle(3,4, '6');
    }
}
```

![image-20241204094400039](attachments/9_Java基础语法7.assets/image-20241204094400039.png)

#### 3、无参有返回值

```
public class TestMethod7 {
    //功能：随机产生1个[0,100)的整数
    public static int getANumberFrom0To100(){//无参有返回值
        return (int)(Math.random()*100);
    }

    public static void main(String[] args) {
        //有返回值的方法调用写完之后，可以 是 方法名().var 来自动生成左边的变量，或者 方法();按Ctrl + Alt + V
        int result = getANumberFrom0To100();
        System.out.println("result = " + result);
    }
}
```

![image-20241204095007380](attachments/9_Java基础语法7.assets/image-20241204095007380.png)

#### 4、有参有返回值

```
public class TestMethod8 {
    //功能：求任意两个整数的最大值
    public static int max(int a, int b){//有参有返回值
        return a > b ? a : b;
    }

    public static void main(String[] args) {
        int x = 4;
        int y = 5;
        int z = 12;

        int bigger = max(x, y);
        System.out.println("bigger = " + bigger);
        int biggest = max(bigger, z);
        System.out.println("biggest = " + biggest);
    }
}
```

## 1.3 方法调用过程内存分析（理解）

### 1.3.1 过程说明

入栈：当方法被调用执行时，JVM会给这个方法在“栈”内存开辟一块`独立的`内存空间，用于存储这个方法的局部变量等信息。

出栈：当这个方法调用结束，JVM会`自动释放`这个方法占用的`栈内存`空间。

栈：先进后出

### 1.3.2 案例1

```
public class TestMethodMemory {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        add(a,b);
        int result = add(a, b);
        System.out.println("result = " + result);
    }

    public static int add(int a, int b){
        int sum = a + b;
        return sum;
    }
}
```

![image-20241204105641104](attachments/9_Java基础语法7.assets/image-20241204105641104.png)

### 1.3.2 案例2

```
public class TestMethodMemory2 {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        reverse(nums);
        for (int i = 0; i < nums.length; i++) {
            System.out.print(nums[i]+" ");
        }
    }
    //实现了数组的反转
    public static void reverse(int[] arr){
        for(int left=0,right=arr.length-1; left<right; left++,right--){
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
        }
    }
}
```

![image-20241204110915054](attachments/9_Java基础语法7.assets/image-20241204110915054.png)

## 1.4 答疑

### 1.4.1 要不要参数

需求：求任意两个整数的和

![image-20241204112631483](attachments/9_Java基础语法7.assets/image-20241204112631483.png)

### 1.4.2 要不要返回值

![image-20241204113016060](attachments/9_Java基础语法7.assets/image-20241204113016060.png)

### 1.4.3 功能划分

- 一个方法同时完成多个功能，复用性低，局限性大
- 一个方法只完成一个功能，复用性好，灵活性好

```
public class TestArray {
    public static void main(String[] args) {
        int[] nums = new int[5];
        sort(nums);
    }

    //一个方法完成多个功能，复用性低，局限性大
    public static void sort(int[] arr){
        //给元素赋值
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random()*100);
        }
        //遍历数组
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        //排序
        for(int i=1; i<arr.length; i++){
            for(int j=0; j<arr.length-i; j++){
                if(arr[j] > arr[j+1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        //遍历数组
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
}
public class TestArray2 {
    public static void main(String[] args) {
        int[] nums = new int[5];
        fill(nums);//给元素赋值
        System.out.println("排序之前：");
        print(nums);//打印元素值
        sort(nums);//排序
        System.out.println("排序之后：");
        print(nums);

        System.out.println("================");

        int[] arr = {2,4,5,1,2};
        System.out.println("排序之前：");
        print(arr);//打印元素值
        sort(arr);//排序
        System.out.println("排序之后：");
        print(arr);

        System.out.println("===============");
        int[] array = {4,5,6,3,1};
        print(array);
    }

    //每一个方法只完成一个功能，复用性好，灵活
    public static void fill(int[] arr){
        //给元素赋值
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random()*100);
        }
    }

    public static void print(int[] arr){
        //遍历数组
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }

    public static void sort(int[] arr){
        //排序
        for(int i=1; i<arr.length; i++){
            for(int j=0; j<arr.length-i; j++){
                if(arr[j] > arr[j+1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}
```

## 1.5 方法的跨类调用

目前咱们都是public static的方法，本类中，方法之间可以直接互相调用。但是跨类调用时，需要加上“类名.”

```
public class DateTools {
    //（1）定义一个isLeapYear方法，可以判断year是不是闰年
    public static boolean isLeapYear(int year){
/*        if(year%4==0 && year%100!=0 || year%400==0){
            return true;
        }else{
            return false;
        }*/

        return year%4==0 && year%100!=0 || year%400==0;
    }

    //（2）定义一个totalDaysOfYear方法，返回year年的总天数
    public static int totalDaysOfYear(int year){
        return isLeapYear(year)? 366 : 365;
    }
    
    /*
    public static void main(String[] args) {
        int year = 2023;
        System.out.println(year +"是闰年吗？" + isLeapYear(year));
        System.out.println(year  +"的总天数：" + totalDaysOfYear(year));
    }
    */

}
public class TestDateTools {
    public static void main(String[] args) {
        int year = 2023;
        System.out.println(year +"是闰年吗？" + DateTools.isLeapYear(year));
        System.out.println(year  +"的总天数：" + DateTools.totalDaysOfYear(year));
    }
}
```

## 1.6 方法的参数传递机制

### 1.6.1 实参给形参传值

- 形参：形式参数
- 实参：实际参数

实参是负责给形参传值，要求实参的类型、个数、顺序 与形参要一一对应。

### 1.6.2 形参的修改是不是会影响实参（理解，会分析代码题即可）

#### 1、参数是基本数据类型

结论：参数是基本数据类型时，实参把数据值copy给形参之后，它们就没关系了。形参无论怎么修改，都与实参无关。

```
public class TestParamDemo1 {
    public static void main(String[] args) {
        int x = 1;
        int y = 2;
        System.out.println("x = " + x +"，y = " + y );
        swap(x,y);
        System.out.println("x = " + x +"，y = " + y );
    }

    public static void swap(int a, int b){
        int temp = a;
        a = b;
        b = temp;
    }
}
```

![image-20241204152114763](attachments/9_Java基础语法7.assets/image-20241204152114763.png)

```
public class TestParamDemo2 {
    public static void main(String[] args) {
        int x= 1;
        System.out.println("x = " + x);
        change(x);
        System.out.println("x = " + x);
    }

    public static void change(int a){
        ++a;
        a=100;
    }
}
```

#### 2、参数是引用数据类型

Java的类，数组等都是引用数据类型，这里用数组演示。

实参给形参的是`首地址的副本`，意味着形参和实参指向同一个对象，所以形参的修改会影响实参。

```
public class TestParamDemo3 {
    public static void main(String[] args) {
        int[] nums = {10,20,30,40,50};
        print(nums);
        swap(nums,0,4);
        print(nums);
    }

    //功能：交换arr数组中 arr[left]与arr[right]的元素
    public static void swap(int[] arr, int left, int right){
        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
    }

    public static void print(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] +" ");
        }
        System.out.println();
    }
}
```

![image-20241204153143156](attachments/9_Java基础语法7.assets/image-20241204153143156.png)

### 1.6.3 形参指向新对象

结论：一旦形参指向新对象，与原来的实参无关了。

![image-20241204155311807](attachments/9_Java基础语法7.assets/image-20241204155311807.png)

```
public class TestParamDemo4 {
    public static void main(String[] args) {
        int[] nums = {1,2,3,4,5};
        print(nums);//1,2,3,4,5
        change(nums);
        print(nums);
        //100,2,3,4,5
    }

    public static void change(int[] arr){
        arr[0] = 100;
        arr = new int[arr.length+1];//让形参指向新的数组对象，接下来arr的任何操作与实参无关了
        arr[0] = 200;
    }

    public static void print(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] +" ");
        }
        System.out.println();
    }
}
```

如果要拿到新数组，就必须返回新数组。

```
public class TestParamDemo4_2 {
    public static void main(String[] args) {
        int[] nums = {1,2,3,4,5};
        print(nums);//1,2,3,4,5
        nums = change(nums);//接收新数组的首地址
        print(nums);
        //100,2,3,4,5
    }

    public static int[] change(int[] arr){
        arr[0] = 100;
        arr = new int[arr.length+1];//让形参指向新的数组对象，接下来arr的任何操作与实参无关了
        arr[0] = 200;
        return arr;//返回新的数组的首地址
    }

    public static void print(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] +" ");
        }
        System.out.println();
    }
}
```

## 1.7 方法的重载(Overload)（掌握，概念要会背）

1、方法的重载：在同一个类中，出现两个方法的`名称相同`，`形参列表不同`，这样的形式称为方法的重载。方法重载与修饰符、返回值类型、方法体无关。

形参列表不同：可以是`个数不同`，`类型不同`，`顺序不同`，不看形参名

2、为什么要重载？

- 方法名见名知意，如果两个方法的功能是相同的，那么它的名称就应该一样

3、重载方法的调用原则

- 先找实参的个数、类型、顺序与形参`完全匹配`的，如果找到了，就可以确定了
- 如果没找到完全匹配的，要找可以`兼容`的，大的类型可以兼容小的类型，例如double可以兼容int

```
public class TestOverload {
    public static void main(String[] args) {
        //把光标放到调用方法的()里面，按快捷键Ctrl + p
        System.out.println(max(4,6));
        System.out.println(max(4.0,6.0));
        System.out.println(max(4,5,2));

        System.out.println(max(4,6.0));
//        System.out.println(max(4.0,6.0,7.0));//找不到最匹配的，也找不到可以兼容的，就报错了
    }

    //求两个整数的最大值
    public static int max(int a, int b) {
        return a > b ? a : b;
    }

    //求3个整数的最大值
    public static int max(int a, int b, int c) {
        int max = a > b ? a : b;
        return max > c ? max : c;
    }

    //求两个小数的最大值
    public static double max(double a, double b) {
        return a > b ? a : b;
    }
}
```

## 1.8 可变参数（会用即可）

可变参数是指参数的个数不确定，可以是0~n个参数值。

可变参数的标记符号：…

可变参数的使用方式，用使用数组的方式使用它即可。

|                   | 可变参数                                              | 数组类型     |
| ----------------- | ----------------------------------------------------- | ------------ |
| 形式（以int为例） | int…                                                  | int[]        |
| 调用时            | 可以传入0~n个元素，也可以直接传入数组                 | 只能传入数组 |
| 限制              | 一个方法最多只能有1个可变参数，而且必须是最后一个形参 | 没有限制     |

```
public class TestVarParam {
    public static void main(String[] args) {
        System.out.println(add(1,2,3,4,5,6));
        System.out.println(add(1,2));
        System.out.println(add(1));
        System.out.println(add());

        int[] arr = {10,20,30,40,50};
        System.out.println(add(arr));
    }

    //定义一个方法，用于求任意个整数的和
    public static int add(int... nums){
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
        }
        return sum;
    }

/*    public static void test(int... nums, int... args){//错误，一个方法不能有2个可变参数

    }*/
}
public class TestVarParam3 {
    public static void main(String[] args) {
        System.out.println(concat("[","]","-","hello","world","java","atguigu"));
        System.out.println(concat("","","-","hello","world","java","atguigu"));
        System.out.println(concat("","",",","hello","world","java","atguigu"));
        System.out.println(concat("[","]",","));
    }

    //实现拼接n个字符串，拼接的时候可以指定开头的符号，结尾的符号，中间连接的符号
    //hello  world  java   atguigu
    //[hello,world,java,atguigu]
    //hello-world-java-atguigu
    public static String concat(String start, String end, String middle, String... args){
        String str = start;

        for (int i = 0; i < args.length; i++) {
            if(i==0){
                str += args[i];
            }else{
                str += middle + args[i];
            }
        }

        str += end;
        return str;
    }
}
```

## 1.9 递归调用

1、递归调用的概念：一个方法自己调用自己。

2、递归调用要注意：必须有出口。意思是满足xxx条件递归，不满足xx条件不递归。如果无条件递归，就会发生StackOverflowError。

![image-20241204172701673](attachments/9_Java基础语法7.assets/image-20241204172701673.png)

```
public class TestRecursion {
    public static void main(String[] args) {
        //求n!
        /*
        假设：f(n)代表n!
            f(n) = n * f(n-1)
         */
        System.out.println(f(5));
        System.out.println(loop(5));

    }

    public static int f(int n){
        if(n>1) {
            return n * f(n - 1);//自己调用自己就叫递归
        }
        return 1;
    }

    public static int loop(int n){//用循环代替递归
        int result = 1;
        for(int i=n; i>=1; i--){
            result *= i;
        }
        return result;
    }
}
```