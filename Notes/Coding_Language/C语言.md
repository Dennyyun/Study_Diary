---
title: C语言
date: 2024-07-13 19:35:39
tags:
categories: 
  - Programming language learning
---



# C 语言

C 语言的一些基础知识

> <font color = red>注：</font> 内容可能不完整！！

<!-- more -->

## 数据类型：

```c
	char 				//字符数据类型
	short		       //短类型
    int					 //整形
    long			   //长整型
    long long		//更长的整形
    float				//单精度浮点类型
    double 			 //双精度浮点类型
        
        //查看每种类型的大小: sizeof()
     printf("%d \n",sizeof(int));
```



## 常量、变量：

### 变量的定义：

```c
int 	age =50;
char  ch="w";
float  weight = 45.5f;
```

### 变量的分类：

- 局部变量
- 全部变量

```c
#include <stdio.h>

//全部变量
int global = 200;

int main() {
    // 局部变量
    int local = 100;;
    //就近原则使用变量
    int global = 50;
    printf("global => %d\n", global);
    return 0;
}
```

![image-20240714134538267](../../images/image-20240714134538267.png)

## 常见的关键字

```c
auto  break   case  char  const   continue  default  do   double else  enum  
extern float  for   goto  if   int   long  register    return   short  signed
sizeof   static struct  switch  typedef union  unsigned   void  volatile  while

```



### 关键词 `typedef`：

> typedef 顾名思义是类型定义，这里应该理解为类型重命名。

```c
//将unsigned int 重命名为uint_32, 所以uint_32也是一个类型名
typedef unsigned int uint_32;

int main()
{
    //观察num1和num2,这两个变量的类型是一样的
    unsigned int num1 = 0;
    uint_32 num2 = 0;
    return 0;
}
```

### `static` 关键字：

> 在C语言中：
>
>  static是用来修饰变量和函数的 
>
> 1. 修饰局部变量-称为静态局部变量 
> 2. 修饰全局变量-称为静态全局变量
> 3.  修饰函数-称为静态函数



1. `static` 修饰局部变量时,局部变量出了作用域,不销毁. 改变了存储位置.影响了变量的生命周期,生命周期变长, 与程序的生命周期一样.
2. ![image-20240714143509419](../../images/image-20240714143509419.png)
