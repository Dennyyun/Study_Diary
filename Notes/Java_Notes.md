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
- 测试类： 用于检查其他类是否书写正确，带有`mian` 方法类，是程序的入口。
- 工具类：不是用与描述事物的类，而是做事情的类。
  1. 类名见名知意
  2. 私有化构造方法。
  3. 方法定义为静态，方便调用。

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

```java
//在Unicode 编码中表示空字符（空白）。
'\u0000'   //可用于char类型表示 空
```



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

### 替换 `replace`

```java
字符串.replace（"需要替换的内容", "替换为新的内容");
```

### `StringBuilder`

> 概述：

`StringBuilder`创建后的**内容是可以改变的**，可以看成是一个容器。

- ==注：其对象不是地址值，而是属性值。==

#### 应用场景

- 拼接字符串的时候
- 反转字符串的时候

#### 构造方法

```java
StringBuilder stringBuilder = new StringBuilder();

StringBuilder stringBuilder = new StringBuilder("abc");
```

#### 常用方法

- `append`： 在末尾追加数据，并返回对象本身。
- `reverse`： 反转容器里的内容。
- `length`： 返回对象长度。
- `toString`：将String Builder转换为String。

### `StringJoiner`

> 与StringBuilder类似,内容可以改变.

#### 构造方法:(两种)

```java
StringJoiner sj = new StringJoiner("分隔符");

StringJoiner sj = new StringJoiner("分隔符","前缀","后缀");
```

#### 方法

- `add()`:添加数据.
- `length()`:返回长度.
- `toString()`: 返回字符串.

## 集合

> 长度不固定

> 只能存储引用**数据类型**, <font color = red>基本数据类型想要存储,需要变成其对应的包装类</font>

### 创建对象

```java
ArrayList<数据类型> strings = new ArrayList<>();
```

### 成员方法

- Boolean `add ()`: 添加元素,返回值表示是否添加成功.
- Boolean `remove ()`: 删除指定元素,返回表示是否是否成功.
- E `remove()`: 删除指定索引的元素,返回被删除的元素.
- E `set(int index, E e)`: 修改指定索引下的元素,返回原来的元素.
- E `get()`: 获取指定索引的元素.
- E `size()`: 集合的长度.

## 面向对象



### `static` 静态变量

static ：表示静态，是java的修饰符，可以修饰成员方法，成员变量。（静态变量、静态方法）

- 静态变量：
  1. 特点：
     - 被该类被所有对象恭喜。
     - <font color = red>不属于对象，属于类</font>
     - <font color = red>随着类的加载而加载，优先于对象存在。</font>
  2. 调用方式：

- 静态方法：
  1. 特点：	
     - 多用在测试类和工具中
     - JavaBean 类中很少会用
  2. 调用方法： 
     - 类名调用（推荐）
     - 对象名调用。

- 工具类：做事情的类,但不描述任何事物的类.

## 继承

- `java` 只支持单继承,不支持多继承,但支持多层继承.

> 什么时候使用继承

==当类与类之间,存在相同(共性)的内容,并满足子类是父类中的一种,就可以考虑使用继承,来优化代码==

### 子类可以继承哪些父类中的内容

| 构造方法 | `非私有`     **不能** | `private`  **不能**   |
| -------- | --------------------- | --------------------- |
| 成员变量 | `非私有`     **能**   | `private`   **能**    |
| 成员方法 | `需方发表`  **能**    | `否则`       **不能** |

### 成员变量访问特点

> ==就近原则:谁离我近,我就用谁.==

### 成员方法的访问特点

- `this`调用:  就近原则 (谁离我近就用谁。)
- `super` 调用：直接访问父类。

### 方法重写

> 重写的方法尽量与父类保持一致。

### 构造方法访问的特点

- 子类不能继承父类的构造方法,但是可以通过`super` 直接调用.
- 子类构造方法的第一行,有一个默认的 `super();`
- 默认先访问父类的无参构造方法,在执行自己.
- 如果想要方法父类有参构造,必须手动写.

## 多态

### 调用成员的特点

- `变量调用`：编译看左边，运行也看左边。
- `方法调用`：编译看左边，运行看右边。

### 优势

- 在多态形式下，右边对象可以实现解耦合，便于拓张和维护。

```java
		// 例
Person p = new Student();  //new Student(); 变更
p.work();	//业务逻辑发生改变时，后续代码无需修改。
```

- 定义方法的时候，使用父类型作为参数，可以接受所有子类对象，体现多态的扩展性与便利。

### 弊端

- 无法调用子类的特有功能。

### 类型转换

> 变回子类类型就可以了

==转换的时候不能瞎转，类型必须一致，否则就会报错==

```java
animal  a  = new Dog(); //自动类型转换
Dog d  = (Dog)  a;		//强制类型转换


if（a    instanceof   Dog）{
//可以判断所记录的对象是不是Dog 类型    
} 
```

强制类型转换可以解决什么问题？

- 可以转成真正的子类型，从调用子类独有功能。
- 转换类型与真实对象类型不一致会报错。
- 转换的时候使用 instanceof  关键字进行判断即可。
