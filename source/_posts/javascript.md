---
title: js
date: 2025-12-12
tags: js
---
JavaScript 是一种广泛应用于网页开发的编程语言，它可以让网页具有交互性和动态功能，JS 分为三部分：ECMAScipt、DOM、BOM，以下简称 js。

JS 的注释：单行注释 ctrl+/;多行注释 shift+alt+a

#### 1 输入输出语句
```js
/* 浏览器弹出警示框 */
alert(msg)
/* 浏览器控制台打印输出信息 */
console.log(msg)
/* 浏览器弹出输入框，用户可以输入 */
prompt(info)
```

#### 2 变量
变量是存放数据的容器，我们通过变量名获取数据，甚至数据可以修改。

**变量的使用**

1.声明变量
var 是 variable 的缩写，声明后计算机自动为变量分配内存空间
```js
var age
```

2.赋值
```js
age = 20 //给 age 这个变量赋值 20
```

**交换两个变量**

交换两个变量，需要用到临时变量 temp
```js
    var temp;
    var apple1 = '青苹果';
    var apple2 = '红苹果';
    temp = apple1;
    apple1 = apple2
    apple2 = temp
    console.log(apple1)
    console.log(apple2)
```

#### 数据类型
JS 是一种弱类型或者说动态语言，这意味着不用提前声明变量的类型，再程序运行过程中，类型会被**自动确定**，相同的变量也可以用作**不同的**类型。比如：
```js
var x = 10;
x = 'reno';
``` 
##### 数字类型分类
**简单数字类型**

Number 0;Boolean false;String;Undefined;Null

程序里的数字前面加 0，表示八进制。前面加 0x，表示十六进制。最大值和最小值。NaN 不是一个数字；Infinity 无穷大，-Infinity 无穷小。
```js
var num1 = 010 //输出 8
var num2 = 0xa //输出 10
console.log(Number.MAX_VALUE);
console.log(Number.MIN_VALUE);
```

