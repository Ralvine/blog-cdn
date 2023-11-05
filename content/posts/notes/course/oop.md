---
authors: [Ralvine]
title: 面向对象程序设计
# subtitle: 副标题.
date: 2023-03-01T20:20:40+08:00
lastmod: 2023-07-01T20:25:40+08:00
draft: false
description: 22-23 春夏学期「面向对象程序设计」课程学习笔记。
#license: MI
images: ["https://z1.ax1x.com/2023/10/23/piAWIwd.png"]
#seriesNavigation: 系列导航.
featuredImage: 
featuredImagePreview: "https://z1.ax1x.com/2023/10/23/piAWIwd.png"
hiddenFromHomePage: false
hiddenFromSearch: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: true
enableLastMod: true
enableWordCount: true
enableReadingTime: true
tags: ["C++", "编程语言", "许威威"]
categories: ["笔记"]
series: ["本科课程"]
series_weight: 1
---

<!--more-->

{{< admonition quote "课程信息" true >}}
🎓 计算机科学与技术学院<br>
🕙 2022-2023 春夏<br>
🧑‍🏫 许威威<br>
📝 50%作业，50%期末
{{< /admonition >}}

## 介绍[^1]

Buzzwords
- 继承
- cohesion 凝聚
- coupling 耦合
- overriding
- interface 接口
- polymorphic 多态
    - polymorphic method calls
- matator methods
- Encapsulation 封装

C的优缺点&C++新特性

## 引用

函数swap操作形参无法交换外部变量，C用指针，C++引入引用。

```c++
int n=4;
int& SetValue() {
    return n;
}
int main() {
    SetValue()=40;
    cout << n;
    return 0;
} // Output: 40.
```

## 常量

区别define，有类型检查。

常量指针，不允许通过指针修改目标内容，但可以改变指向对象。

在函数形参中使用，防止形参被修改

常量成员函数：不应修改其所作用的对象（除了静态成员变量）

常量对象 `const Sample o;` 不可修改对象，但是可以执行其中的常量成员函数。

成员函数名字参数相同，有无const的区别属于重载关系。（实例对象是否常量决定了调用哪个成员函数）

常引用：对象作函数参数，为了避免复制构造函数降低效率，直接用引用，而为了防止实参跟着变，采用常引用。

## 动态内存分配

分配变量：`int* P; P=new T;`

T是任意类型名，相当于开辟了sizeof(T)的空间，P是指向它起始地址的指针，即T*.

释放：只能delete一次，对数组应为`delete [] p;`

不delete就不会释放！

## 内联函数、重载和缺省参数

函数调用存在开销，调用本身耗时，内联函数在编译时直接插入函数内操作本身，但程序体积会变大。

`inline int func(parameter) {}`

函数名字相同但参数个数或类型不同，叫做重载。使函数命名简单，编译器自动判断调用哪个函数。二义性，调用函数的参数匹配不上。

缺省参数，最右边连续若干个参数可有缺省值。

`void func(int x1, int x2=2, int x3=3) {}`

## 类和对象

C语言：结构化程序设计，程序=数据结构+算法，但函数和操作的数据结构没有直接联系，规模增大后难以理解、扩充、查错。

C++：面向对象程序

指针方式：`ClassName* p= &AClassObject`，用 - > 指向其成员变量或函数。

引用方式：`ClassName& p= AClassObject` 同时跟着变。

私有成员：缺省=private，同Class其他对象的私有成员也可访问。

成员函数也可重载、参数缺省。

## 构造函数

一个类可以有多个构造函数。

对象数组，注意动态分配时没定义就不初始化。

复制构造函数，参数必须引用`X::X(X& x)`；起作用：直接`Complex c2(c1)`，或者函数参数或返回值含有该类对象；但是对象间赋值不会调用复制构造函数。

常量引用参数：减少开销，确保实参值不变时使用。

类型转换构造函数：只含一个参数。

析构函数：有对象数组情况下，程序结束时每个元素都会调用析构函数；临时对象和形参对象消亡都会调用。

局部对象：`{ 生命周期 }`，静态对象static：函数结束时不消亡。

不同编译器输出有所差别，有的做了优化，赋值可以不用再临时生成被复制的对象。

## this指针

C++编译先翻译成C时，Class变为Struct，因此需要多一个this指针指向函数作用的对象。因此可以返回对象自身。

静态成员函数则不可使用this指针，因为其不具体作用于某个对象。

## 静态成员变量

静态成员为所有对象共享，总共就一份。sizeof()计算对象时不会计算其static成员变量。

访问方式。需要在定义类的文件中单独进行声明或初始化！

静态成员**函数**还可以直接通过整个类进行调用。

本质是全局变量，只是放在类中。例：方体类的实例总数。

⬆️缺陷，若实例对象是复制构造生成的，Total会有遗漏，特别是临时对象消亡时还会调用析构函数，因此需要单独写一个复制构造函数。

静态成员**函数**不能调用非静态的成员变量或函数。

## 成员对象和封闭类

Class中有成员变量为其他Class类型，即称其为成员对象。例如Class Car下有成员变量Engine，属于Engine类。

初始化列表：构造函数后直接赋值。

先执行封闭类下所有对象成员构造函数，再执行封闭类构造函数；析构时顺序相反。

## 友元

友元类，关系不能传递和继承。

## 运算符重载

根据参数数目决定重载为成员函数或普通函数

赋值运算符的重载：以string为例，需要防止指向同一块内存。

此时返回对象需要引用，如`String&`：应当保留运算符原本特性，使得允许a=b=c和(a=b)=c.

还需要防止s=s.

还需要为其写单独的复制构造函数。

若声明时直接赋值，属于调用构造函数。

[^1]: 智云课堂回放 https://classroom.zju.edu.cn/coursedetail?course_id=50910&tenant_code=112
[^2]: 面向对象MOOC https://www.bilibili.com/video/BV1ob411q7vb/
[^3]: 笔记 @Ryan
