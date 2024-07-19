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

### `static`

> <font color =red>注意事项</font>

- 静态方法**只能**访问静态变量和静态风法
- 非静态方法可以**访问**静态变量或者静态方法，**也可以**访问非静态的成员变量和非静态的成员方法
- 静态方法中是没有this关键字

总结：

1. 静态方法中，只能访问静态。
2. 非静态可以访问所有。
3. 静态方法中没有`this` 关键字

#### `static` 静态变量

> 决定是否使用 `static`，是否需要<font color =red>共享！</font>

static ：表示静态，是java的修饰符，可以修饰成员方法，成员变量。（静态变量、静态方法）

- 静态变量：
  1. 特点：
     - 被该类被所有对象共享。
     - <font color = red>不属于对象，属于类</font>
     - <font color = red>随着类的加载而加载，优先于对象存在。</font>
  
  2. 调用方式：
  
     - 类名调用（推荐）
  
     - 对象名调用。
  
       

#### `static`静态方法

- 静态方法：
  1. 特点：	
     - 多用在测试类和工具中
     - JavaBean 类中很少会用
  2. 调用方法： 
     - 类名调用（推荐）
     - 对象名调用。
- 工具类：做事情的类,但不描述任何事物的类.

### 继承

- `java` 只支持单继承,不支持多继承,但支持多层继承.

> 什么时候使用继承

==当类与类之间,存在相同(共性)的内容,并满足子类是父类中的一种,就可以考虑使用继承,来优化代码==

#### 子类可以继承哪些父类中的内容

| 构造方法 | `非私有`     **不能** | `private`  **不能**   |
| -------- | --------------------- | --------------------- |
| 成员变量 | `非私有`     **能**   | `private`   **能**    |
| 成员方法 | `需方发表`  **能**    | `否则`       **不能** |

#### 成员变量访问特点

> ==就近原则:谁离我近,我就用谁.==

#### 成员方法的访问特点

- `this`调用:  就近原则 (谁离我近就用谁。)
- `super` 调用：直接访问父类。

#### 方法重写

> 重写的方法尽量与父类保持一致。

#### 构造方法访问的特点

- 子类不能继承父类的构造方法,但是可以通过`super` 直接调用.
- 子类构造方法的第一行,有一个默认的 `super();`
- 默认先访问父类的无参构造方法,在执行自己.
- 如果想要方法父类有参构造,必须手动写.

### 多态

#### 调用成员的特点

- `变量调用`：编译看左边，运行也看左边。
- `方法调用`：编译看左边，运行看右边。

#### 优势

- 在多态形式下，右边对象可以实现解耦合，便于拓张和维护。

```java
		// 例
Person p = new Student();  //new Student(); 变更
p.work();	//业务逻辑发生改变时，后续代码无需修改。
```

- 定义方法的时候，使用父类型作为参数，可以接受所有子类对象，体现多态的扩展性与便利。

#### 弊端

- 无法调用子类的特有功能。

#### 类型转换

> 变回子类类型就可以了

==转换的时候不能瞎转，类型必须一致，否则就会报错==

```java
animal  a  = new Dog(); //自动类型转换
Dog d  = (Dog)  a;		//强制类型转换


if（a    instanceof   Dog）{
//可以判断所记录的对象是不是Dog 类型    
} 
```

制类型转换可以解决什么问题？

- 可以转成真正的子类型，从调用子类独有功能。
- 转换类型与真实对象类型不一致会报错。
- 转换的时候使用 instanceof  关键字进行判断即可。

### final （最终）

- `final` 修饰变量：==叫做**常量**，只能被赋值一次。==
	1. <font color=red>本数据类型：变量的值无法改变。</font>
	2. <font color=red>引用数据类型：地址值无法改变，内部属性值可以修改。</font>
- `final` 修饰方法：==表明该方法为最终方法，不能被重写。==
- `final`修饰类：==表明该类为最终类，无法被继承。==

#### 常量

> 注：<font color=red>**单个单词：**</font>**全部大写**；<font color=red>**多个单词：**</font>**全部大写，单词之间用下划线隔开。**

### 权限修饰符

| 修饰符    | 同一个类中 | 同一个包中其他类 | 不同包下的子类 | 不同包下的无关类 |
| --------- | ---------- | ---------------- | -------------- | ---------------- |
| private   | &#10004;   |                  |                |                  |
| 空着不写  | &#10004;   | &#10004;         |                |                  |
| protected | &#10004;   | &#10004;         | &#10004;       |                  |
| public    | &#10004;   | &#10004;         | &#10004;       | &#10004;         |

### 代码块

- 静态代码块

  1. 格式：**static{}**
  2. 特点：需要通过static 关键字修饰，随着类的加载而加载，并且自动触发，只执行一次。
  3. 使用场景：在类加载的时候，做一些数据初始化的时候使用。




### 抽象类、抽象方法

- 抽象类不能实例化
- 抽象类中不一定有抽象方法，有抽象方法的类一定是抽象类。
- 可以有构造方法
- 抽象类的子类
  - 要么重写抽象类中的的所有抽象方法
  - ~~*要么抽象类*~~



#### 抽象类的作用

1. 抽取共性时，无法确定方法体，就把方法体定义为抽象的。
2. 强制让子类按照某种格式重写。
3. 抽象方法所在的类，必须是抽象类。

#### 格式

```java
//抽象方法
public abstract  返回值类型  方法名  (参数列表);

//抽象类
public abstract  class  类名 {}
```



#### 继承抽象的注意事项

- 要么重写抽象类中的的所有抽象方法
- ~~*要么抽象类*~~

### 接口

接口是一个行为的规则

#### 接口的定义和使用

- 接口用关键字`interface`来定义

  ```java
  public interface 接口名 {}
  ```

- 接口不能实例化

- 接口和类之间是实现关系，通过 `implements` 关键字表示

  ```java
  public class 类名 implements 接口名 {}
  ```

- 接口的子类（实现类）

  - 要么重写接口中的所有抽象方法
  - 要么是抽象类

> 接口和类实现关系， 可以单实现，也可以多实现。
>
> ```java
> public class 类名 implements 接口名1， 接口名2{}
> ```
>
> 实现类还可以在继承一类的同时实现多个接口。
>
> ```java
> public class 类名 extends 父类 implements 接口名1， 接口名2{}
> ```
>
> 



#### 接口里面成员的特性

- 成员变量
  1. 只能是常量
  2. 默认修饰符：<font color=red>**public**</font> static final 
- 构造方法
  - 没有
- 成员方法
  1. 只能是抽象方法
  2. 默认修饰符： public abstract
- <font color=red>JDK7以前：</font>接口中只能定义抽象方法。



#### 接口和类之间的关系

- 类和类的关系

  - 继承关系、只能单继承、不能多继承、但是可以多层继承

- 类和接口的关系

  - 实现关系、可以单实现、也可以多实现、还可以在继承一个类的同时实现多个接口

- 接口和接口的关系

  - 继承关系、可以单继承、也可以多继承

  >细节：如果实现类实现了最下面的子接口，那么就需要重写所有的抽象方法

#### 接口中的默认方法定义格式

```java
public default 返回类型  方法名 (参数列表){}
```

- 默认格式注意事项：
  1. 默认方法不是抽象方法，所以不强制被重写。但是如果被重写，重写时去掉`default` 关键字
  2. `public`可以省略， `default`不能省略
  3. 如果实现了多个接口，多个接口中存在相同名字的默认方法，子类就必须对该方法重写。

##### `JDK8` 以后接口中新增的方法

- 允许在接口中定义静态方法，需要用`static`修饰

###### 接口中静态方法定义格式：

- 格式：

  ```java
  public static 返回值类型 方法名（参数列表）{}
  
  public static void show () {}
  ```



##### `JDK9` 新增的方法

接口中私有方法的定义格式：

- 格式1：普通私有方法

  ```java
  private 放回值类型 方法名(){}
  
  private voide show(){}
  ```

- 格式2：静态私有方法

  ```java
  private static void  show(){}
  ```

  

#### 接口的应用

1. 接口代表规则，是行为的抽象。想要让哪个类拥有一个行为，就让这个类事项对应的接口就可以了。
2. 当一个方法的参数是接口时，可以传递接口所实现类的对象，这种方法称之为接口多态。



#### 适配器设计模式

1. 当一个接口中抽象方法过多，但是只要使用其中一部分的时候，就可以适配器模式。
2. 书写步骤：
   - 编写中间类 <font color=red>`XXXAdapter`</font>，实现对应的接口。
   - 对接口中的抽象方法进行空实现。
   - 让真正的实现类继承中间类，并重写需要的方法。
   - 为了避免其他类创建适配器类的对象，中间的适配器类用`abstract`进行修饰

### 内部类

> 类的五大成员：
>
> ​	属性、方法、构造方法、代码块、内部类

1. <font color=red>什么是内部类:</font>
   -  在一个类里面的类就叫做内部类。
2. <font color=red>什么时候用到内部类:</font>
   - B类表示的事物是A类的一部分，且B单独存在没有意义。
   - 比如：汽车的发动机，ArrayList的迭代器，人的心脏等



####  内部类的分类

按定义的位置来分

1. **成员内部内**，类定义在了成员位置 (类中方法外称为成员位置，无static修饰的内部类)
2. **静态内部类**，类定义在了成员位置 (类中方法外称为成员位置，有static修饰的内部类)
3. **局部内部类**，类定义在方法内
4. **匿名内部类**，没有名字的内部类，可以在方法中，也可以在类中方法外。

##### 内部类访问特点：

- 内部类可以直接访问外部类的成员，包括私有
- 外部类要访问内部类的成员，必须创建对象

#### 成员内部类

**成员内部类特点**：

- 无static修饰的内部类，属于外部类对象的。
- 宿主：外部类对象。

**内部类的使用格式**：

```java
 外部类.内部类。 // 访问内部类的类型都是用 外部类.内部类
```

**获取成员内部类对象的两种方式**：

方式一：外部直接创建成员内部类的对象

```java
外部类.内部类 变量 = new 外部类（）.new 内部类（）;
```

方式二：在外部类中定义一个方法提供内部类的对象

**案例演示**

```java
方式一：
public class Test {
    public static void main(String[] args) {
        //  宿主：外部类对象。
       // Outer out = new Outer();
        // 创建内部类对象。
        Outer.Inner oi = new Outer().new Inner();
        oi.method();
    }
}

class Outer {
    // 成员内部类，属于外部类对象的。
    // 拓展：成员内部类不能定义静态成员。
    public class Inner{
        // 这里面的东西与类是完全一样的。
        public void method(){
            System.out.println("内部类中的方法被调用了");
        }
    }
}


方式二：
public class Outer {
    String name;
    private class Inner{
        static int a = 10;
    }
    public Inner getInstance(){
        return new Inner();
    }
}

public class Test {
    public static void main(String[] args) {
        Outer o = new Outer();
        System.out.println(o.getInstance());

    }

}

```

#### 成员内部类的细节

编写成员内部类的注意点：

1. 成员内部类可以被一些修饰符所修饰，比如： private，默认，protected，public，static等
2. 在成员内部类里面，JDK16之前不能定义静态变量，JDK16开始才可以定义静态变量。
3. 创建内部类对象时，对象中有一个隐含的Outer.this记录外部类对象的地址值。（请参见3.6节的内存图）

详解：

​	内部类被private修饰，外界无法直接获取内部类的对象，只能通过3.3节中的方式二获取内部类的对象

​	被其他权限修饰符修饰的内部类一般用3.3节中的方式一直接获取内部类的对象

​	内部类被static修饰是成员内部类中的特殊情况，叫做静态内部类下面单独学习。

​	内部类如果想要访问外部类的成员变量，外部类的变量必须用final修饰，JDK8以前必须手动写final，JDK8之后不需要手动写，JDK默认加上。

####  成员内部类面试题

请在?地方向上相应代码,以达到输出的内容

注意：内部类访问外部类对象的格式是：**外部类名.this**

```java
public class Test {
    public static void main(String[] args) {
        Outer.inner oi = new Outer().new inner();
        oi.method();
    }
}

class Outer {	// 外部类
    private int a = 30;

    // 在成员位置定义一个类
    class inner {
        private int a = 20;

        public void method() {
            int a = 10;
            System.out.println(???);	// 10   答案：a
            System.out.println(???);	// 20	答案：this.a
            System.out.println(???);	// 30	答案：Outer.this.a
        }
    }
}
```

#### 成员内部类内存图

![内部类内存图](../../../Hexo/workspace/source/images/内部类内存图.png)

#### 静态内部类

**静态内部类特点**：

* 静态内部类是一种特殊的成员内部类。

- 有static修饰，属于外部类本身的。
- 总结：静态内部类与其他类的用法完全一样。只是访问的时候需要加上外部类.内部类。
- **拓展1**:静态内部类可以直接访问外部类的静态成员。
- **拓展2**:静态内部类不可以直接访问外部类的非静态成员，如果要访问需要创建外部类的对象。
- **拓展3**:静态内部类中没有银行的Outer.this。

**内部类的使用格式**：

```
外部类.内部类。
```

**静态内部类对象的创建格式**：

```java
外部类.内部类  变量 = new  外部类.内部类构造器;
```

**调用方法的格式：**

* 调用非静态方法的格式：先创建对象，用对象调用
* 调用静态方法的格式：外部类名.内部类名.方法名();

**案例演示**：

```java
// 外部类：Outer01
class Outer01{
    private static  String sc_name = "黑马程序";
    // 内部类: Inner01
    public static class Inner01{
        // 这里面的东西与类是完全一样的。
        private String name;
        public Inner01(String name) {
            this.name = name;
        }
        public void showName(){
            System.out.println(this.name);
            // 拓展:静态内部类可以直接访问外部类的静态成员。
            System.out.println(sc_name);
        }
    }
}

public class InnerClassDemo01 {
    public static void main(String[] args) {
        // 创建静态内部类对象。
        // 外部类.内部类  变量 = new  外部类.内部类构造器;
        Outer01.Inner01 in  = new Outer01.Inner01("张三");
        in.showName();
    }
}
```

#### 局部内部类

- **局部内部类** ：定义在**方法中**的类。

定义格式:

```java
class 外部类名 {
	数据类型 变量名;
	
	修饰符 返回值类型 方法名(参数列表) {
		// …
		class 内部类 {
			// 成员变量
			// 成员方法
		}
	}
}
```

#### 匿名内部类（IMP）

#####  概述

**匿名内部类** ：是内部类的简化写法。他是一个隐含了名字的内部类。开发中，最常用到的内部类就是匿名内部类了。

##### 格式

```java
new 类名或者接口名() {
     重写方法;
};
```

包含了：

* 继承或者实现关系

* 方法重写
* 创建对象

所以从语法上来讲，这个整体其实是匿名内部类对象

##### 什么时候用到匿名内部类

**实际上，如果我们希望定义一个只要使用一次的类，就可考虑使用匿名内部类。匿名内部类的本质作用**

**是为了简化代码**。 

之前我们使用接口时，似乎得做如下几步操作：

1. 定义子类
2. 重写接口中的方法
3. 创建子类对象
4. 调用重写后的方法

```java
interface Swim {
    public abstract void swimming();
}

// 1. 定义接口的实现类
class Student implements Swim {
    // 2. 重写抽象方法
    @Override
    public void swimming() {
        System.out.println("狗刨式...");
    }
}

public class Test {
    public static void main(String[] args) {
        // 3. 创建实现类对象
        Student s = new Student();
        // 4. 调用方法
        s.swimming();
    }
}
```

我们的目的，最终只是为了调用方法，那么能不能简化一下，把以上四步合成一步呢？匿名内部类就是做这样的快捷方式。

##### 类前提和格式

匿名内部类必须**继承一个父类**或者**实现一个父接口**。

**匿名内部类格式**

```java
new 父类名或者接口名(){
    // 方法重写
    @Override 
    public void method() {
        // 执行语句
    }
};
```

##### 使用方式

以接口为例，匿名内部类的使用，代码如下：

```java
interface Swim {
    public abstract void swimming();
}

public class Demo07 {
    public static void main(String[] args) {
        // 使用匿名内部类
		new Swim() {
			@Override
			public void swimming() {
				System.out.println("自由泳...");
			}
		}.swimming();

        // 接口 变量 = new 实现类(); // 多态,走子类的重写方法
        Swim s2 = new Swim() {
            @Override
            public void swimming() {
                System.out.println("蛙泳...");
            }
        };

        s2.swimming();
        s2.swimming();
    }
}
```

##### 匿名内部类的特点

1. 定义一个没有名字的内部类
2. 这个类实现了父类，或者父类接口
3. 匿名内部类会创建这个没有名字的类的对象

##### 匿名内部类的使用场景

通常在方法的形式参数是接口或者抽象类时，也可以将匿名内部类作为参数传递。代码如下：

```java
interface Swim {
    public abstract void swimming();
}

public class Demo07 {
    public static void main(String[] args) {
        // 普通方式传入对象
        // 创建实现类对象
        Student s = new Student();
        
        goSwimming(s);
        // 匿名内部类使用场景:作为方法参数传递
        Swim s3 = new Swim() {
            @Override
            public void swimming() {
                System.out.println("蝶泳...");
            }
        };
        // 传入匿名内部类
        goSwimming(s3);

        // 完美方案: 一步到位
        goSwimming(new Swim() {
            public void swimming() {
                System.out.println("大学生, 蛙泳...");
            }
        });

        goSwimming(new Swim() {
            public void swimming() {
                System.out.println("小学生, 自由泳...");
            }
        });
    }

    // 定义一个方法,模拟请一些人去游泳
    public static void goSwimming(Swim s) {
        s.swimming();
    }
}
```

