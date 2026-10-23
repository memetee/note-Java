#  一、复习

## 1.1 一维数组

一维数组的标记符号：[]

一维数组的静态初始化：

```
元素的类型[]  数组名 = {元素值1, 元素值2, 元素值3};
元素的类型[]  数组名;
数组名 = new  元素的类型[]{元素值1, 元素值2, 元素值3};
```

一维数组的动态初始化：

```
元素的类型[]  数组名 = new 元素的类型[长度值]; //写完这句数组里面的元素是默认值
数组名[下标] = 具体值; //这里的具体值，可能是一个计算表达式，可能是键盘输入，可能是随机产生，....
byte：0
short：0
int：0
long：0L
float：0.0F
double：0.0
char：'\u0000' 或 编码值为0的空字符
boolean：false
String等引用数据类型：null
```

一维数组的遍历：

```
for(int i=0; i<数组名.length; i++){ //自动生成这个for结构的快捷键  数组名.fori 或 itar
    数组名[i]代表元素
}
```

## 1.2 二维数组

```
二维数组的标记符号：[][]
```

二维数组的静态初始化：

```
元素的类型[][]  数组名 = {{元素值1, 元素值2, 元素值3}, {元素值1, 元素值2, 元素值3}, {元素值1, 元素值2, 元素值3}};
//每一组的元素个数可以不同
元素的类型[][]  数组名;
数组名 = new  元素的类型[][]{{元素值1, 元素值2, 元素值3}, {元素值1, 元素值2, 元素值3}, {元素值1, 元素值2, 元素值3}};
二维数组的声明：
    元素的类型[][]  数组名; //标准
	元素的类型  数组名[][];
 	元素的类型[]  数组名[];
```

二维数组的动态初始化：

（1）规则的矩阵：每一组的元素个数相同，或每一行的长度是相同

```
元素的类型[][]  数组名 = new 元素的类型[总行数][每一行的长度]; 
例如：
    int[][] arr = new int[5][10]; 
	//代表有5行，每一行有10个元素，共50个元素
byte：0
short：0
int：0
long：0L
float：0.0F
double：0.0
char：'\u0000' 或 编码值为0的空字符
boolean：false
String等引用数据类型：null
```

（2）不规则的二维表：每一组的元素个数不一定相同，或每一行的长度不一定相同

```
元素的类型[][]  数组名 = new 元素的类型[总行数][];  //这一步只确定了几行，比喻，盖房子，只是打了地基，每一层楼还没盖
												//数组名[下标]都是null
数组名[0] = new 元素的类型[第1行的长度]; //比喻：盖了一楼，[第1行的长度]决定了这层楼有几个房间，此时房间里面都是默认值
数组名[1] = new 元素的类型[第2行的长度];
```

二维数组的遍历：

```
for(int i=0; i<数组名.length; i++){ //自动生成这个for结构的快捷键  数组名.fori 或 itar
    //数组名[i]代表某一行
    for(int j=0; j<数组名[i].length; j++){
        //数组名[i][j]代表一个元素
    }
}
```

# 二、一维数组的算法（续）

## 2.1 在数组中查找最大值、最小值

### 1、数组是静态初始化的（掌握，必选）

```
public class TestArrayMax {
    public static void main(String[] args) {
        int[] arr = {5, 6, 2, 7, 8, 1, 3};

        //故事：猴子掰最大的玉米
        //思路：
        //（1）先假设第1个元素是最大的
        int max = arr[0];

        //（2）用后面的元素与max比较，有比max大的，就替换max变量的值
        //这里i从1开始，表示元素的查找范围是[1, arr.length-1]，把[0]排除了
        for(int i=1; i<arr.length; i++){
            if(arr[i] > max){
                max = arr[i];
            }
        }
        System.out.println("max = " + max);
    }
}
public class TestArrayMin {
    public static void main(String[] args) {
        int[] arr = {5, 6, 2, 7, 8, 1, 3};

        //故事：猴子掰最小的玉米
        //思路：
        //（1）先假设第1个元素是最小的
        int min = arr[0];

        //（2）用后面的元素与min比较，有比min小的，就替换min变量的值
        //这里i从1开始，表示元素的查找范围是[1, arr.length-1]，把[0]排除了
        for(int i=1; i<arr.length; i++){
            if(arr[i] < min){
                min = arr[i];
            }
        }
        System.out.println("min = " + min);
    }
}
```

### 2、数组是动态初始化（拓展，可选）

```
public class TestArrayMax4 {
    public static void main(String[] args) {
        //元素是随机产生的,(-100,0]
        int[] arr = new int[10];//写完这句数组里面的元素是默认值，int类型的默认值是0

        //解决方案一：先产生所有的随机数
        for (int i = 0; i < arr.length; i++) {
            arr[i] = -(int) (Math.random() * 100);
            System.out.print(arr[i] + " ");
        }
        //到这里为止，元素值已经是确定的了

        int max = arr[0];//这一行代码 max =第1个元素的值
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] > max){
                max = arr[i];
            }
        }
        System.out.println("max = " + max);
    }
}
public class TestArrayMax5 {
    public static void main(String[] args) {
        //元素是随机产生的,
        int[] arr = new int[10];//写完这句数组里面的元素是默认值，int类型的默认值是0

        //解决方案二：产生随机数的同时，就找最大值
        int max = 0;//随便初始化一个
        for (int i = 0; i < arr.length; i++) {
//            arr[i] = -(int) (Math.random() * 100);
            arr[i] = (int) (Math.random() * 100);
            System.out.print(arr[i] + " ");
            
            if(i==0){//第1个元素的时候
                max = arr[0];//把max修改为第1个元素
            }else if(arr[i] > max){//不是第一个元素，让它与max比大小
                max = arr[i];
            }
        }

        System.out.println("max = " + max);
    }
}
```

## 2.2 在数组中查找最值及其下标

### 1、元素不重复（掌握，必选）

两种写法，选择一种来熟悉和掌握

```
public class TestArrayMaxIndex {
    public static void main(String[] args) {
        int[] arr = {5, 6, 2, 7, 8, 1, 3};

        //定义两个变量，一个代表最大值，一个代表最大值的下标
        int max = arr[0];//max是最大值
        int index = 0; //index是下标
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] > max){
                max = arr[i];
                index = i;
            }
        }
        System.out.println("max = " + max);
        System.out.println("index = [" + index +"]");
        System.out.println("第" + (index+1) +"个最大");
    }
}
public class TestArrayMaxIndex2 {
    public static void main(String[] args) {
        int[] arr = {5, 6, 2, 7, 8, 1, 3};

        //定义1个变量
        int index = 0; //index是下标，最大值的下班
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] > arr[index]){
                index = i;
            }
        }
        System.out.println("max = " + arr[index]);
        System.out.println("index = [" + index +"]");
        System.out.println("第" + (index+1) +"个最大");
    }
}
```

### 2、元素重复（拓展，可选）

```
public class TestArrayMaxIndex3 {
    public static void main(String[] args) {
        int[] arr = {5, 6, 8, 7, 8, 9, 3, 9};

        /*
        方案一：（1）先找出最大值（2）再遍历数组，看哪些元素与最大值相同，打印它们的下标
         */
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] > max){
                max = arr[i];
            }
        }
        System.out.println("max = " + max);

        //看哪些元素与最大值相同，打印它们的下标
        System.out.println("最大值的下标有：");
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] == max){
                System.out.print("[" + i +"] ");
            }
        }
    }
}
public class TestArrayMaxIndex4 {
    public static void main(String[] args) {
        int[] arr = {5, 6, 8, 7, 8, 9, 3, 9};

        /*
        方案二：
        (1)假设max表示最大值，初始化为arr[0]
        (2)假设maxIndexStr表示最大值的下标，它是String，初始化为"0"

         */
        int max = arr[0];
        String maxIndexStr = "0";
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] > max){
                max = arr[i];
                maxIndexStr = i + "";
            }else if(arr[i] == max){
                maxIndexStr += "," + i;
            }
        }
        System.out.println("max = " + max);
        System.out.println("maxIndexStr = [" + maxIndexStr+"]");
    }
}
```

## 2.3 在数组查找目标值

### 1、顺序查找（掌握，必选）

```
import java.util.Scanner;

public class TestArrayOrderFind {
    public static void main(String[] args) {
        int[] arr = {5, 6, 2, 7, 8, 1, 3};

        //从键盘输入一个整数，看它在不在数组中
        Scanner input = new Scanner(System.in);

        System.out.print("请输入一个整数：");
        int target = input.nextInt();//7  or  9

        //用target与数组的元素“一一比较”，确定是否存在
        boolean flag = false;//假设它不存在，flag是一个标记值，false代表不存在，true代表存在
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] == target){
                flag = true;
                break;
            }
        }

       if(flag){// if(flag==true){
            System.out.println("找到了");
        }else{
            System.out.println("没找到");
        }

        input.close();
    }
}
```

思考题：如果数组是有序的，例如：从小到大，那么上面的顺序查找可以优化吗？

```
import java.util.Scanner;

public class TestArrayOrderFind2 {
    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 12, 24};//数组是有序的情况下

        //从键盘输入一个整数，看它在不在数组中
        Scanner input = new Scanner(System.in);

        System.out.print("请输入一个整数：");
        int target = input.nextInt();//7  or  8

        //用target与数组的元素“一一比较”，确定是否存在
        boolean flag = false;//假设它不存在，flag是一个标记值，false代表不存在，true代表存在
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {//找到目标
                flag = true;
                break;
            }else if(arr[i] > target){//提前确定不存在
                break;
            }
        }

        if (flag) {// if(flag==true){
            System.out.println("找到了");
        } else {
            System.out.println("没找到");
        }

        input.close();
    }
}
```

### 2、二分查找（拓展，可选）

前提：有序

![image-20241203115330539](attachments/8_Java基础语法6.assets/image-20241203115330539.png)

结论：

- 顺序查找时间复杂度是O(n)
- 二分查找时间复杂度是O(logn)

```
import java.util.Scanner;

public class TestBinarySearch {
    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 12, 24};//数组是有序的情况下

        Scanner input = new Scanner(System.in);

        System.out.print("请输入要查找的目标值：");
        int target = input.nextInt();

        //无序数组不能用以下二分查找
        int index = -1;//初始值是-1，因为正常下标不会是-1
        int left = 0;//第一个元素的下标
        int right = arr.length - 1;//最后一个元素的下标
        //left ,right, mid，index都是下标
        while(left <= right){//当left > right就需要结束
            int mid = left + (right-left)/2; //或者  mid = (left + right)/2;
            if(target == arr[mid]){
                index = mid;
                break;
            }else if(target > arr[mid]){//去右边
                //修改左边界
                left = mid + 1;
            }else{//target < arr[mid] 去左边
                //修改右边界
                right = mid - 1;
            }
        }

        if(index == -1){
            System.out.println("不存在");
        }else{
            System.out.println("存在");
        }
        input.close();
    }
}
```

## 2.4 数组反转

```
public class TestArrayReverse {
    public static void main(String[] args) {
        int[] arr = {5, 6, 7, 2, 1};
        //反转后 {1,2,7,6,5}

        System.out.print("交换之前：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        //方案一：对称位置的元素交换
        for(int left = 0,right = arr.length-1; left < right; left++,right--){
            //arr[left] ~ arr[right] 交换
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
        }

        System.out.print("交换之后：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

    }
}
public class TestArrayReverse2 {
    public static void main(String[] args) {
        int[] arr = {5, 6, 7, 2, 1};
        //反转后 {1,2,7,6,5}

        System.out.print("交换之前：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        //方案二：定义一个新数组
        int[] newArr = new int[arr.length];
        //把arr数组的元素  倒序 放到newArr中
        for (int i = 0; i < arr.length; i++) {
            newArr[arr.length-1-i] = arr[i];
        }
        arr = newArr;

        System.out.print("交换之后：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

    }
}
```

## 2.5 数组的排序

### 1、冒泡排序（掌握，必选）

```
public class TestBubbleSort2 {
    public static void main(String[] args) {
        int[] arr = {2, 8, 6, 3, 1,7,4,3,2};

        for(int i=1; i<arr.length; i++) {//代表一共有几轮
            //为什么-i？因为每一轮比上一轮少一个元素参与
            for (int j = 0; j < arr.length - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]+" ");
        }
        System.out.println();

    }
}
```

冒泡排序的推导过程：

![image-20241203150014467](attachments/8_Java基础语法6.assets/image-20241203150014467.png)

```
public class TestBubbleSort {
    public static void main(String[] args) {
        int[] arr = {2, 8, 6, 3, 1};
        
        /*
        第一轮：[0] ~ [4]
        [0] ~ [1]
        [1] ~ [2]
        [2] ~ [3]
        [3] ~ [4]
        j=0,1,2,3,     j+1=1,2,3,4
         */
        for (int j = 0; j < arr.length - 1; j++) {
            if(arr[j] > arr[j+1]){
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }

        System.out.println("第一轮结束：");
        for (int j = 0; j < arr.length; j++) {
            System.out.print(arr[j]+" ");
        }
        System.out.println();

        /*
        第二轮：[0] ~ [3]
        [0] ~ [1]
        [1] ~ [2]
        [2] ~ [3]
        j=0,1,2      j+1=1,2,3
         */
        for (int j = 0; j < arr.length - 2; j++) {
            if(arr[j] > arr[j+1]){
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println("第二轮结束：");
        for (int j = 0; j < arr.length; j++) {
            System.out.print(arr[j]+" ");
        }
        System.out.println();

       /*
        第三轮：[0] ~ [2]
        [0] ~ [1]
        [1] ~ [2]
        j=0,1,      j+1=1,2
         */
        for (int j = 0; j < arr.length - 3; j++) {
            if(arr[j] > arr[j+1]){
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println("第三轮结束：");
        for (int j = 0; j < arr.length; j++) {
            System.out.print(arr[j]+" ");
        }
        System.out.println();

        /*
        第四轮：[0] ~ [1]
        [0] ~ [1]
        j=0 ,    j+1=1
         */
        for (int j = 0; j < arr.length - 4; j++) {
            if(arr[j] > arr[j+1]){
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println("第四轮结束：");
        for (int j = 0; j < arr.length; j++) {
            System.out.print(arr[j]+" ");
        }
        System.out.println();
    }
}
```

思考题：能不能优化冒泡排序的代码？

```
public class TestBubbleSort3 {
    public static void main(String[] args) {
        int[] arr = {1,2,3,5,4};

        /*
        思考：如果提前已经排好序了，没必要非得执行n-1轮？
        换一个问题：如何通过代码检测数组已经排序好？
         */

        for(int i=1; i<arr.length; i++) {
            boolean flag = true;//true代表已经排好序了
            for (int j = 0; j < arr.length - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;

                    flag = false;//可能还未排好序
                }
            }

            if(flag){
                break;//结束外循环
            }
        }

        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]+" ");
        }
        System.out.println();
    }
}
```

### 2、选择排序（拓展，可选）

```
public class TestSelectSort {
    public static void main(String[] args) {
        int[] arr = {5, 6, 3, 4, 1};

        //外循环控制几轮，n个元素，需要n-1
        //arr.length=5, i=0,1,2,3
        for(int i=0; i<arr.length-1; i++){
            //查找本轮的最小值及其下标
            int min = arr[i];//本轮第1个元素
            int index = i;

            //后面的元素与min比较
            for(int j=i+1; j<arr.length; j++){
                if(arr[j] < min){
                    min = arr[j];
                    index = j;
                }
            }

            //看一下本轮最小值在不在[i]的位置
            if(index != i){
                //交换arr[i] 与 arr[index]位置的元素
                int temp = arr[i];
                arr[i] = arr[index];
                arr[index] = temp;
            }
        }

        System.out.println("排序后：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]+" ");
        }
    }
}
```

## 2.6 数组的扩容（拓展，可选）

数组的特点：一旦长度确定，就无法更改了。

数组扩容的思路：再创建一个更大的数组，然后把原来数组中的元素搬过去（复制过去）

```
import java.util.Scanner;

public class TestArrayGrow {
    public static void main(String[] args) {
        //一开始，数组的长度为5，从键盘输入整数放到数组中，不断输入，直到输入0为止
        int[] arr = new int[5];

        Scanner input = new Scanner(System.in);

        int count = 0;//输入的数字的个数
        while(true){
            System.out.print("请输入整数：");
            int num = input.nextInt();

            if(num == 0){
                break;
            }else{
                //放到数组中
                arr[count] = num;
                count++;

                //扩容
                if(count >= arr.length){
                    //再创建一个更大的数组
//                    int[] newArr = new int[arr.length+1];//扩1个位置
//                    int[] newArr = new int[arr.length*2];//2倍扩容
//                    int[] newArr = new int[(int)(arr.length*1.5)];//1.5倍
//                    int[] newArr = new int[arr.length + arr.length/2];//1.5倍
                    int[] newArr = new int[arr.length + (arr.length>>1)];//1.5倍

                    //把数组原来的元素copy到新数组中
                    for(int i=0; i<arr.length; i++){
                        newArr[i] = arr[i];
                    }

                    //让arr指向新数组
                    arr = newArr;
                }
            }
        }


        input.close();
    }
}
```

## 2.7 数组元素的插入（拓展，可选）

```
import java.util.Scanner;

public class TestArrayInsert {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};

        //从键盘输入1个整数，插入到arr数组的[1]位置
        //（1）先扩容
        int[] newArr = new int[arr.length+1];//扩1个位置
        for(int i=0; i<arr.length; i++){//原样复制元素
            newArr[i] = arr[i];
        }
        arr = newArr;//抛弃旧数组，选用新数组

        //(2)把[1]位置及其后面的元素往右移动
        /*
        [4] -> [5]
        [3] -> [4]
        [2] -> [3]
        [1] -> [2]
         */
        for(int i=arr.length-1; i>1; i--){
            //arr[后面] = arr[前面];
            arr[i] = arr[i-1];
        }



        //（3）在[1]插入新元素
        Scanner input = new Scanner(System.in);
        System.out.print("请输入新元素：");
        int newNum = input.nextInt();

        arr[1] = newNum;

        input.close();

        //（4）遍历数组
        System.out.println("插入新元素之后：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]+" ");
        }
    }
}
```

## 2.8 数组元素的删除（拓展，可选）

```
public class TestArrayDelete {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};

        //删除元素20，并且要保证剩下的元素仍然是连续存储
        //(1)把[1]位置及其后面的元素往前移动
        /*
        [2] -> [1]
        [3] -> [2]
        [4] -> [3]
         */
        //arr.length=5,  i=1,2,3
        for(int i=1; i<arr.length-1; i++){
//            arr[前面] = arr[后面];
            arr[i] = arr[i+1];
        }

        //(2)把末尾位置置0
        arr[arr.length-1] = 0;

        System.out.println("删除20元素后：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]+" ");
        }

    }
}
```