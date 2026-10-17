
## 计算机组成（了解）

<img src="attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126092434687.png" alt="image-20241126092434687" style="zoom: 50%;" />

## 几个DOS命令（了解）

![image-20241126092545557](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126092545557.png)



## 编程语言介绍（了解）

![image-20241126101915454](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126101915454.png)

![image-20241126102951369](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126102951369.png)

![image-20241126103449682](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126103449682.png)



## Java环境搭建（必会操作）

### JDK的安装

略

### 环境变量的配置

#### 环境变量的作用

环境：Java程序运行的环境，例如操作系统就是一个环境。

变量：它是用一个单词代表一个值，这个值可以修改，例如：name代表姓名 name = "柴林燕";  name = "宋红康";

操作系统也是一个程序，里面也有很多值需要存储，所以就有环境变量的说法。其中一个非常重要的环境变量是path变量。

path：路径，它代表程序的安装路径。

`配置环境变量path就是让操作系统可以找到这个程序`。

拿到一个jdk安装包，可以选择一个路径进行安装，这里是安装到了d盘。

![image-20241126104918874](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126104918874.png)

#### 找到path环境变量

![image-20241126105000563](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105000563.png)

![image-20241126105024920](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105024920.png)

![image-20241126105114553](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105114553.png)

#### 删除path中自动添加的javapath值

![image-20241126105310470](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105310470.png)

![image-20241126105336693](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105336693.png)

![image-20241126105447108](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105447108.png)

#### 新增JAVA_HOME环境变量

![image-20241126105732328](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105732328.png)

#### 在path中配置JAVA_HOME

![image-20241126105837205](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126105837205.png)



## HelloWorld程序

### 步骤

第一步：用编辑器（可以是记事本，可以是notepadd++，可以是editplus等）编写代码

第二步：编译

第三步：运行



### 编写代码

首先，所有代码必须写到类中

```java
public class 类名{
    //
}
```

```java
public class HelloWorld{//类
	public static void main(String[] args){//主方法
		System.out.println("atguigu");//输出语句
	}
}
```



<img src="attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126113216701.png" alt="image-20241126113216701" style="zoom: 67%;" />



### 编译（javac）

编译的目的是把Java代码进行初加工，加工为JVM能认识的字节码。

![image-20241126113427053](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126113427053.png)

![image-20241126113552914](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126113552914.png)

命令格式：

```java
javac  xx.java
```



### 运行（java）

![image-20241126113725159](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126113725159.png)

![image-20241126114126792](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126114126792.png)

命令格式：

```java
java  主类名
```

> 主类：是指包含main方法的类。



## 一些问题

### 类名与源文件名不一致的问题

如果加了public，那么 public 类名 和 文件名 不一致，那么无法编译

![image-20241126115529427](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126115529427.png)



如果删掉类名前面的public，那么类名和文件名可以不一致

![image-20241126115637936](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126115637936.png)

虽然，只要类不是public，类名和源文件名可以不一致，但是不推荐这么干，不利于后期代码的维护。

### 乱码问题

![image-20241126115835016](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126115835016.png)

![image-20241126115920916](attachments/1_Java%E5%9F%BA%E7%A1%80%E6%A6%82%E8%BF%B0.assets/image-20241126115920916.png)





