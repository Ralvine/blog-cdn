---
authors: [Ralvine]
title: 数据结构与算法
# subtitle: 副标题.
date: 2021-09-01T20:20:40+08:00
lastmod: 2021-09-01T20:25:40+08:00
draft: false
description: 21-22 秋冬学期「数据结构与算法」课程学习笔记。
#license: MI
images: ["https://z1.ax1x.com/2023/10/23/piAW5eH.png"]
#seriesNavigation: 系列导航.
featuredImage: 
featuredImagePreview: "https://z1.ax1x.com/2023/10/23/piAW5eH.png"
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
tags: ["C++", "数据结构", "王何宇", "专业必修"]
categories: ["笔记"]
series: ["本科课程"]
series_weight: 1
---

<!--more-->

{{< admonition quote "课程信息" true >}}
🎓 数学科学学院<br>
🕙 2021-2022 秋冬<br>
🧑‍🏫 王何宇<br>
📝 作业，项目作业，期末考试
{{< /admonition >}}

{{< admonition note "课程材料" true >}}
- 《Mathematical Foundations for Data Analysis》Jeff M. Phillips
{{< /admonition >}}

{{< admonition note "课程大纲" true >}}
- CH3. 链表、栈和队列
- CH4. 树
- CH5. 哈希
- CH6. 优先队列和堆
- CH7. 分类
- CH8. *
- CH9. 图
- Extra. 主定理
{{< /admonition >}}

## C++ 基础知识

###  动态内存与释放

```c++
char* name; delete [] name;
Birds() {name=new char[256]}
```

利用指针实现动态内存分配。同值对象指向相同address

Shell命令查看内存泄漏状况`valgrind filename`

释放内存：及时delete变量。由于为指针，要防止指向新地址时原内存未被释放。

### template

编译时自动填充typename
在类外撰写类成员函数时需要添加
可指定T的具体类型

```c++
template<typename T>
Array<T>::FunctionName(const Array<T>& _obj) {}
```

### 关键字修饰符

#### const

对成员函数：修饰非静态数据，只读化。应尽可能将该成员函数声明为const 成员函数，除非成员函数需要修改数据成员。const可访问非常量数据，反之不可。指针数据可以被const 函数修改。
`Class:: func() const {}`

对形参：指针传递，禁止修改指针指向地址内存数据；值传递不需要const保护。

`void copyMemory(const T* _s,T* _d,int _n);`

#### static

静态变量，延长生命周期又相较全局变量保留了一定的访问范围。需要一个数据对象为整个类而非某个对象服务,同时又力求不破坏类的封装性,即要求此成员隐藏在类的内部时使用。

#### *this

指向obj自身的指针

#### explicit 显式转换

`explicit` 对单参数构造函数限制隐式转换
防止编译器进行类型等方式的强制转换。

### 宏定义

用于简化重复语句`#define TEMP template<typename T>`

编译处理

```c++
#ifndef xxx
#define xxx
#else
#endif
```

### 传递 引用

#### 形参的值传递 指针传递 引用传递

默认为值传递，开辟新函数，储存实参数据；指针实质存在一层中介地址，引用传递直接对传入对象进行修改；

`*&obj` 适用于struct对象，对其属性变量进行修改

1. `T* a` ： 传递实参指针地址，及最终指向数据地址，但可以利用*a修改地址内存数据
2. `T& a` ：左值引用，实参的别名

#### 左值 右值引用

右值引用 `&&` ：防止传递给形参 `T& a` 的是常量（此时函数无法修改a）

**看能不能对表达式取地址，如果能，则为左值，否则为右值**

```c++
int a = 10;
const int c = 10;
int &d = c; // error.
int &&d = 10;
```

**约定** rhs：引用；lhs：赋值

### std::move

强制将左值转换为右值引用，如 `push_back` 避免开辟新内存

```c++
AvlNode(const Comparable & ele, AvlNode *lt, AvlNode *rt, int h = 0): element{ele}, left{lt}, right{rt}, height{h} {}
AvlNode(Comparable && ele, AvlNode *lt, AvlNode *rt, int h = 0): element{std::move(ele)}, left{lt}, right{rt}, height{h} {} //参数无地址，临时ele=参数
```

### Class & Struct 封装

外部只提供相应功能的接口，不允许直接对底层对象进行修改。

#### 复制构造函数

将b中成员属性复制到c： `Birds c(b);`
类中处理：定义拷贝函数；否则：缺省。
需要开辟新的动态内存

```c++
Birds(Birds _obj) {
name=new char [256]; 
for循环迭代载入name[i]=_obj.name[i];
}
```

#### 函数化

如复制构造函数中的copyMemory，便于多核并行运算。

#### struct 定义传入参数

使得struct能够直接在定义时传入相应参数

`BinaryNode(const Comparable& theElement, BinaryNode *lt, BinaryNode *rt): element(theElement),left(lt),right(rt) {}`

#### Operator 重载运算符

```
const Array& operator=(const Array& _obj)
```

### 注释

doxymacs/doxygen格式的注释：
可以通过命令提取所有相应注释以html方式直观显示。

### Standard Template Library

```c++
// get random number.
srand((unsigned)time(nullptr)); // 随机种子
a=rand()%10;
```

```c++
#include <algorithm>
abs();min();max();swap(a,b);
#include <cmath>
sqrt();sin();cos();tan();pow();
#include <ctime>
clock_t start = clock();
```

## 复杂度

### big O

$1000N=O(N^2); (logN)^k=O(N);$

$1 < logN < N < NlogN < N^2$

### 时间复杂度

- for循环｜内语句*迭代次数；嵌套循环
- 顺序语句｜求和，取Max；判定语句
- NlogN|最大子序列问题 一次N遍历&一次二分查找
- logN｜二分搜索，欧几里得

## 主定理

**归纳法证明：** 

（例）

**一般性证明：**

构造树，$\text{depth}=log(b,n)，\text{widget}=a^{(log(b,n))}=n^{(log(b,a))}$

{{< admonition note "实例：二分查找" true >}}
$T(n) = T(n/2) + O(1)$

$T(n/2) = T(n/4) + O(1)$

$...$

$T(2) = T(1) + O(1)$

$T(1) = O(1)$

$a=1,b=2,k=0$ 代入得 $O(logN)$;
{{< /admonition >}}




另可直接证，由于为$1/2,1/4...1/n$, 尾项$2^k$项为$n$，故共$logn$项，$$T(n)=logn\times o(1)=logn$$


## Vector & List & Stack & Queues

### iterator 

```c++
std::vector<int> iterator a=A.begin();
i = find(v.begin(), v.end(), 1);
```

### Vector & List

- Array | 经典数组
- Vector | 批量分配内存的数组，空间不够时再申请新的内存；模板化`<T>`；允许拷贝赋值
- List | 链表 Single/Double-Linked-List **双链表** 表头、尾、哨兵结点

```c++
vector<int> a(10,1); //10个初值为1的元素
vector<int> a(b.begin(),b.begin+3);

//共有
a.clear();a.empty();
a.front();a.back();
a.push_back(1);a.size();
a.resize(10,2);//现有元素数目调整,多删少补,未给定参数2则随机

// Vector
a[i];a.insert(a.begin()+1,5);
a.pop_back();a.swap(b);
a.reserve(100);//容量

// List
a.push_front(val);a.insert(single_val);
a.remove(val);a.remove_if(condition);a.unique();//去重
```

| 类型               | Access | Insert | Delete | Search |
| ------------------ | ------ | ------ | ------ | ------ |
| Array/Vector       | 1      | n      | n      | n      |
| Single-linked-List | n      | 1      | 1      | n      |
| Double-linked-List | n      | 1      | 1      | n      |

### Stack & Queue

`pop() push() size() swap() empty();`

- Stack: LIFO `top();` 
- Queue: FIFO `front() back();`

#### Stack 计算器

- 前缀/后缀。
- **中缀转后缀：**`A+B*(C-D)-E/F`转为`ABCD−∗+EF/−`

优先级设置 `‘*’ = ‘/’ > ‘+’ = ‘-’ >`
- style1: `‘(’` 优先级最高，如直接读入；推入操作符时不弹
- style2: `‘(’` 优先级最低，强制直接读入
- 数字直接放到[输出列]，右括号直接弹到左括号止；
- 操作符：栈弹出直到遇到比自己优先级低的操作符再入栈。
- 计算：顺序读取，数字入栈，符号弹出两数字运算，结果入栈。


## 树

Binary Tree 二叉树平均深度 $O(\sqrt{N})$ ，表达式树应用；

### 二叉搜索树

左小右大；平均深度 $O(logN)$ ，最坏深度 $O(N-1)$.

#### 构建

- `contains`｜`findMin(Max)`｜`insert`｜`～` 
- `makeEmpty` 递归
- `copy` | clone，递归 `return new node`; 
- 重载运算符：`this!=&rhs` 则 `makeEmpty` 再 `clone rhs.root` ，最终 `return *this`
- `remove` | `(*&t)t` 为结点地址；空, `return`; `t<>x` 判断; `t=x`.
- 双子: `t->ele=findmax(t->right)->ele` , `remove(t->ele;t->right); // 右子找min代入t,删除该min`
- 单子/无子: `T*oldNode=t` ,另引入的参数 `t=t->left/right` 相当于改结点地址为 t 左/右子，再删 `oldNode` 即删了原结点.

```c++
// findmin: 递归或while 注意空树直接返回nullptr
BinaryNode * findMin( BinaryNode *t ) const {
  if( t == nullptr )
    return nullptr;
  if( t->left == nullptr )
    return t;
  return findMin( t->left );
}
// insert
1.if t==nullptr:new node{x,nullptr,nullptr};
2.else compare x,t->ele,递归
3.balance and update the height(max(subtree)+1).
```

#### 关于 struct 构造

- `BinaryNode` 置于 private；针对 `struct` 的操作也位于 private 部分
- 外部操作 $\rightarrow$ public函数 $\rightarrow$ private函数

#### 关于 function 参数

对 `Struct BinaryNode`，由于其 `element` 为变量，`left/right` 为指针，fuction 引用时应采用 `BinaryNode * & t` ，引用 Node 地址。

#### 时间分析

- 内部路径长｜所有结点的深度和
- 递推关系、秩，(average) $$D(N)=D(i)+D(N-i-1)+N-1 \Rightarrow O(NlogN)$$

- 任意结点预期深度 $logN$
- 交替 `insert/remove` $O(N^2)$ ，期望深度 $O(\sqrt{N})$

### Balance 树

```c++
/// Height 处理
// Binary Tree
int height( BinaryNode *t ) { 
  if( t == nullptr )
    return -1;
  else
    return 1 + max(height(t->left), height(t->right));
}
// AVL Tree: Struct AvlNode has added the val 'height'.
int height( AvlNode *t ) const {
  return t == nullptr ? -1 : t->height;
}
```

#### AVL 树

每个结点的左子树和右子树高度最多差1（空树为-1）

**Rotation的具体实现**

| 插入方式 | 描述                | 旋转方式     |
| -------- | ------------------ | ------------ |
| LL       | 在a的**左子树**根节点的**左子树**上插入节点而破坏平衡 | 右旋转       |
| RR       | 在a的**右子树**根节点的**右子树**上插入节点而破坏平衡 | 左旋转       |
| LR       | 在a的**左子树**根节点的**右子树**上插入节点而破坏平衡 | 先左旋后右旋 |
| RL       | 在a的**右子树**根节点的**左子树**上插入节点而破坏平衡 | 先右旋后左旋 |



```c++
// insert. 伪代码
x<t->ele:左插入，insert(x,t->left),此时判定
  if balance condition:height of left-right>1;
    then if x<t->left->ele 即LL，对t调用右旋 // 其余同理
// right rotation. (for LL-insert style)
void rotateWithLeftChild( AvlNode * & k2 ) {
  AvlNode *k1 = k2->left;
  k2->left = k1->right;
  k1->right = k2;
  // after rotation , update the height.
  k2->height = max( height( k2->left ), height( k2->right ) ) + 1;
  k1->height = max( height( k1->left ), k2->height ) + 1;
  k2 = k1;
}
// LR-insert.
void doubleWithLeftChild( AvlNode * & k3 ) {
  rotateWithRightChild( k3->left );
  rotateWithLeftChild( k3 );
}
```

**时间复杂度分析**

- 计算高度O(logN)；
- 保证查询O(logN)避免Binary Tree最坏的N；
- 但由于旋转存在，操作效率低，特别是remove时可能需要一直旋转到根；
- 额外封装，繁琐。

*另一种写法：独立的balance操作*

```c++
// at the end of each insert or remove operation, you need to do "balance(t)"
static const int ALLOWED_IMBALANCE = 1;
void balance( AvlNode * & t ) { 
  if( t == nullptr ) 
    return;
  if( height( t->left ) - height( t->right ) > ALLOWED_IMBALANCE )
    if( height( t->left->left ) >= height( t->left->right ) ) 
      rotateWithLeftChild( t ); 
    else 
      doubleWithLeftChild( t );
  else if( height( t->right ) - height( t->left ) > ALLOWED_IMBALANCE ) 
    if( height( t->right->right ) >= height( t->right->left ) ) 
      rotateWithRightChild( t ); 
    else
      doubleWithRightChild( t );
  t->height = max( height( t->left ), height( t->right ) ) + 1; 
}
```

#### Splay 树*

保证从空树开始任意连续M次操作最多花费 $O(MlogN)$ 的时间

### Traversals

```c++
// 前序
文件路径展开
// 中序 O(N)
if( t != nullptr ) { 
    printTree( t->left, out );
    out << t->element << endl; 
    printTree( t->right, out ); 
}
// 后序 O(N)
高度计算
// 层序
using <queue>
```

### B 树*

### Sets & Maps

- Sets｜排序、去重

```c++
set<int> a;
a.find(val);//logN
a.erase(val);a.swap(b);a.clear();
```

- Maps｜key-value(>=1)

```c++
map<int> a;
map<int>::iterator b; // key:b->first; value:b->second....
```

## 哈希

- 散列表
- `insert` / `search` / `delete`
- average:O(1)
- Key -> Table
- 素数
- TableSize
- collision

### 分析

**负数补偿？**

- value<0，then+tableSize

**均匀分配键：**

- 单元数目有限，键数实际上无穷
- 习惯：0～tableSize-1
- 装填因子
- 分离链接法（缺点：内存分配耗时）
- 除了链表，也可用二叉树/新散列表

### 开放寻址法

- 冲突解决函数，$\lambda<0.5$ 聚集效应, $f(i)$ 为冲突点与探查点的距离
- 线性探测: $f(i)=i$ ；一次聚集-占据单元形成区块
- 平方探测: $f(i)=i^2$ 二次聚集
    
    *保证表的大小是素数，否则表被填满一半就找不到空单元了*
    
- 双散列:f(i)=i*hash(x),结果不可以为0；example，hash(x)=R-(xmodR)

### 再散列

- $O(N)$
- 一半/插满的策略
- 途中策略：某一装填因子

### 可扩散列*

## Priority Queues & Heaps

### 二叉堆

- 完全二叉树
- 最小堆、最大堆
- 数组存储 $i,2i,2i+1$
- 查找 $O(N)$
- 堆序性质

**为何选用Heap？**
- Min/Max: $O(1)$

```c++
void insert( const Comparable & x ) {
  // check size.
  if( currentSize == array.size( ) - 1 ) 
    array.resize( array.size( ) * 2 );
  // Percolate up 
  int hole = ++currentSize;
  Comparable copy = x;
  array[ 0 ] = std::move( copy );
  for( ; x < array[ hole / 2 ]; hole /= 2 )
    array[ hole ] = std::move( array[ hole / 2 ] ); // 规避大量交换
  array[ hole ] = std::move( array[ 0 ] );
} 
```

### Applications of Priority Queues

## 排序

### 插入排序

### 快排

#### Pivot策略

**最好/坏可能性**

- 随机选择待排序序列中的一个数字作为划分字问题的标准，划分是否平均影响算法复杂度
- 每次问题规模减半，$a=2，b=2，d=1$
- 复杂度为 $n^2 log(n)$
- 最差情况下，复杂度为 $O(n^2)$

#### 选择的线性期望时间算法

### 线性时间排序: Bucket Sort and Radix Sort 复杂度分析

### 计（基）数排序——非比较算法

- 对于待排序的整数序列，从最低位到最高位每次按照相应的位排序一次
- 每次递归问题规模变为原来的1/10，但需要求解10个子问题，额外运算为 $O(n)$ 的，$a=10，b=10，d=1$
- 复杂度为 $n^1 log(n) = nlog(n)$ ，近似为 $O(kN)$ ，k为整数的位数

### 归并排序/堆排序

归并排序
- 数据列均分为两部分，分别排序，之后以 $O(n)$ 的复杂度进行合并，空间复杂度 $O(n)$
- 每次问题规模减半，$a=2，b=2，d=1$
- 复杂度为 $nlog(n)$



## 图论

- G[graph] -> V[vertex]
- E[edge(arc)], path
- digraph 有向
- Weight&cost 权/值
- Adjacent 邻接
- cycle 回路：满足 $w1=wN$ , length>=1
- loop 环：回到自身，length=0
- Simple path 简单路径
- 强/弱连通、基础图/完全图

### 表示

- Adjacent Matrix：dense `A[u][v]`
- Adjacent List：sparse $O(|E|+|V|) $

### 拓扑排序

```find indegree=0 v1 
-> delete v1, neighbors indegree-1 
-> find indegree=0 v2
...
```

- $O(V^2)$ using `<Queue>`

### Dijkstras

### 最坏可能

### 可对负边权使用的算法

### 最小生成树

- 如何扩张？（Ch10）

### 深度优先 广度优先

## 算法设计补充

### 贪心算法

- ch10.1 分析复杂度

### 分治算法 Divide-and-Conquer

- 分而治之，递归

### Dynamic Programming

- ch10.3 与d-c的比较（自底向上&自顶向下）

### 回溯法