# Denny‘s  Java Notes

## 方法（method）

### 方法定义

```java
//静态方法   可直接调用 test()
public static void test（）{
	//方法体
}
```



```java
//非静态方法  object.test()
public viod test(){
	//方法体
}

```



#### 参数

> 形参:  形式参数,指在方法中<font size=4 color=red>***定义***</font>的参数

> 实参:  实际参数,指方法<font color=red size=4>***调用***</font>中的参数

==注:参数类型必须一致==

#### 返回值方法

```java
public static 返回值类型 test(){
	//方法体;
	return ;
}
```

#### 方法的重载

> ==在同一类中,方法名相同,参数不同,与返回值无关.==

==参数不同:== 个数不同,类型不同,顺序不同

## 内存分配

- 栈： 方法运行时使用的内存，方法进栈运行，运行结束就出栈。
- 堆： `new`出来的，都在堆内存中开辟了一小空间。

### 基本数据类型：

> 数据值是存储在自己的空间里

- <font color =red>特点</font>：赋值给其他变量，也是赋的真实的值。

### 引用数据类型：

> 数据值是存储在其他空间里的，自己空间存储的是地址值

- <font color = red> 特点</font>：赋值给其他变量，赋的是地址值。

## 二维数组

### 静态初始化

> 示例1:

```java
// 数据类型 [][] 数组名 = new 数据类型 [][]{{元素1,元素2},{元素1,元素2}};
int [][] arr = new int [][] {
		    {元素1,元素2},
		    {元素1,元素2}
};
```

> 示例2:

```java
//数据类型 [][] 数组名 = {{元素1,元素2},{元素1,元素2}};
int [][] arr = {
			    {元素1,元素2},
                {元素1,元素2}
};
```

#### 数组的遍历

> 首先遍历**第一遍**,获得二维数组里**一维数组**的==*地址值*==, 第二次遍历获取每一位数组的==*下标*==,再通过下标打印出每个数组里的值.

```java
int[][] arr = new int[][]{
                {12, 34, 56},
                {12, 34, 65, 34}
        };

for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + "\t");
            }
            System.out.println();
        }
```

结果如下: ![image-20240127165601275](https://cdn.jsdelivr.net/gh/Dennyyun/Study_Diary/images/image-20240127165601275.png)

### 动态初始化

> 示例: 

```java
int [][] arr = new int [m][n]
```

- M:	表示这个二维数组的长度, <font color = red>**即表示可存放多少个一维数组**</font>
- N:        表示一维数组的长度, <font color=red>**即表示可以存放多少个元素**</font>

## 类 与 对象

- 类： 具有共同的特征的描述。
- 对象： 真实存在的具体实例。

创建对象示例：

```java
类名  对象名 = new 类名(); 
```

### 类的注意事项

- `JavaBean` 类： 描写一切事物的类。

- 测试类： 编写`mian` 方法类。

> 成员变量：代表属性。

> 成员方法：代表行为。

### 封装

> 注意：<font color =red >对象代表什么，就必须封装对0应的数据，并提供数据对应的行为。</font>

### 构造方法

特点：

- 方法必须与类名一样，没有返回值，（不能由 return 带回结果数据 ）

==注意：==

- <font color = red>如果没有定义构造方法，系统会提供一个默认的无参构造方法。</font>
- <font color = red>如果定义了构造方法，这系统不会提供无参构造方法。</font>

执行时机：

1. 创建对象有虚拟机调用，不能手动调用。
2. 每创建一个对象，就会调用一次构造方法。



## 字符串（String）

### 常用的类型：

```java
//第一种
String str = "abc";
   
//第二种
char [ ] ch ={'a','b','c'}
String str = new String(ch)	//将其拼接成abc
    
    //第三种
byte[ ] bytes = {97,98,99,100};\
 String str = new String(bytes);//将其转换为字符串并拼接
```

### 字符串的比较

> 基本数据类型比较的是数据值

```java
int a = 12;
int b = 10;
sout(	a	==	b	); 	//false
```

> 引用数据类型比较的是地址值

```java
String s1 = new String 	("avb");
String s2 = new String	 ("avb");
sout( s1 == s2) ;	//false
```

#### 比较方法：

```java
//两者相同，只不过一个区分大小写，一个不区分大小写
//equals
String a = "abc";
String b = "ABC";
a.equals( b );  //false

//equalsIgnoreCase
a.equalsIgnoreCase( b );  //true
```

### 遍历字符串

```java
//根据索引返回字符
public char charAt（）
字符串对象.charAt(索引);

//返回字符串的长度
public int length（）
字符串对象.length（）
```

> `Char` 类型的变量在参与计算时，类型会自动提升为 `int`  ，查询`ASCII` 表

### 截取 `substring()`

```java
//		截取以beginIndex开头到endIndex 结尾的字符(不包含endIndex) 左闭右开
String substring(int beginIndex, int endIndex);
   
//从 endIndex 开始截取到末尾;
String substring(int endIndex);
```

