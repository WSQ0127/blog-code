---
title: 517编程普及组数学之二进制
categories: OI
tags:
  - OI
  - 517coding
  - 数学
  - 二进制
abbrlink: a8eee40e
date: 2024-04-16 17:53:08
cover: https://image.wsq127.top/file/2d96852321e1d46e5becf.png
password: 517coding.com
---
---
## 写在最前

> 二进制是计算机内部运算中采用的进制，在这样的进制系统下，只有 ![0,1](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)$0,1$ 两个数字，计算机内部的所有运算（包括位运算)都是在二进制的基础上进行的。

## 原码、反码与补码

### 原码

第一位是符号位，`0` 表示正数，`1` 表示负数，其余位是数值位，正常二进制。

$[+11]=[00001011]原$

$[-11]=[10001011]原$​

原码是人脑最容易理解和计算的表示方式。

### 反码

正数的反码是其本身；

负数的反码是在其原码的基础上，符号位不变，其余各个位取反。

$[+11]=[00001011]原=[00001011]反$

$[-11]=[10001011]原=[11110100]反$​

### 补码

正数的补码是其本身；

负数的补码是在其反码的基础上 $+1$​。

$[+11]=[00001011]原=[00001011]补$

$[-11]=[10001011]原=[11110101]补$

#### 使用

具体演变过程，我不细讲了，感兴趣自行 Bing。

我们只需要知道，在计算机中，数字是以补码的形式存在的。

$2 - 1 = 2 + (-1) = [0000 0010]原+ [1000 0001]原= [1000 0011]原= -3$

如果用原码表示，让符号位也参与计算，显然对于减法来说，结果是不正确的。

$2 - 1 = 2 + (-1) = [0000 0010]原+ [1000 0001]原= [0000 0010]反+ [1111 1110]反= [0000 0000]反= [0000 0000]原= 0$

发现用反码计算减法，仍然是有问题的。

$2 - 1 = 2 + (-1) = [0000 0010]原+ [1000 0001]原= [0000 0011]补 [1111 1111]补= [0000 0001]补= [0000 0001]原= 1$

而用补码计算，运算结果是正确的。

## 位运算

### 按位与、或、异或

| 运算 | C++ 运算符 | 数学符号 |                             解释                             |
| :--: | :--------: | :------: | :----------------------------------------------------------: |
|  与  |    `&`     |    $     | 只有两个对应位都为 $1$ 时才为 ![1](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)$1$ |
|  或  |    `|`     |    \|    | 只要两个对应位中有一个 $1$ 时就为 ![1](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)$1$ |
| 异或 |    `^`     | $\oplus$ |                 只有两个对应位不同时才为 $1$                 |

注意：与逻辑与 $\and$ 和逻辑或 $\or$ 区分。

异或运算的逆运算是它本身，也就是说两次异或同一个数最后结果不变，即 $a\oplus b\oplus b=a$。

### 取反

字面意思，当前位是 $1$ 取反后则是 $0$，反之同理。

取反暂时并没有数学符号，他在 C++ 中的运算符为 `~`。

### 位移

位移包括左移和右移：

* 左移：在 C++ 中的运算符为 `<<` ，`<<n`表示向左移动 $n$ 位。
* 右移：同理，在 C++ 中的运算符为 `>>` ，`>>n`表示向右移动 $n$​ 位。

对于位移，溢出的位将被舍弃，而原先没有数的位置会用 $0$​​ 替补。

### lowbit

还有一个很好玩的东西叫做 lowbit，它的作用是求出一个数最低位的 `1` 在从右往左第几位。

实现起来很简单`(x&-x)`，有没有感觉很神奇？甚至不相信？

让我们验算以下，以 $x=14$ 为例：

* $14=[00001110]原=[00001110]补$
* $-14=[10001110]原=[11110010]补$
* $[00001110]\&[11110010]=[00000010]=2$​

原理：对于 $x$，$-x$ 用反码表示就是全部取反了，包括符号位，而补码则是再加一，而加一后最后一个 `0` 也就是原码中最后一个 `1` 就会变成 `1` 和原来的 `&` 后就会得到这一位。