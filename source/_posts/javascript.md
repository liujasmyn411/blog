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
###### 简单数字类型**

Number 0;Boolean false;String;Undefined;Null

1. Number-数值型
程序里的数字前面加 0，表示八进制。前面加 0x，表示十六进制。最大值和最小值。NaN 不是一个数字；Infinity 无穷大，-Infinity 无穷小。用 isNaN 来判断非数字，是数字返回 false 不是数字返回 true。
```js
var num1 = 010 //输出 8
var num2 = 0xa //输出 10
console.log(Number.MAX_VALUE);
console.log(Number.MIN_VALUE);
console.log(isNaN(12));
console.log(isNaN(我是reno));
```
2. String-字符串型
字符串引号嵌套，单双引号交替使用。
字符串转义符，都是用\开头的，\n是换行符，\t缩进，\b空格。
1) 检测字符串长度 length
```js
var str1 = "my name is Reno";
console.log(str1.length);//输出 15
```
2) 字符串拼接 +
数值和数值拼接是运算，其余数据类型都可以拼接，变量要写在引号外
```js
console.log("沙漠" + "骆驼");//输出沙漠骆驼
var reno = Undefined
console.log("reno" + 1) //输出 NaN
var ageR = 20
console.log("Reno 今年" + ageR + "岁");
```
3. Boolean
运算时，true 当作 1，false 当作 0
```js
var flag1 = true; 
var flag2 = false;
console.log(flag1 + 1);//输出 2
console.log(flag2 + 1);//输出 1
```
4. Undefined 和 Null
如果变量声明却未赋值，输出 Undefined
```js
var year = null
console.log(year + 1);//输出 1
```

###### 获取变量数据类型-typeof

prompt 取过来的数据是字符型的
```js
var num3 = 10;
console.log(typeof num3);//输出 number

var num4 = null;
console.log(typeof num4);//输出 object

var num5 = prompt('请输入您的年龄')
console.log(num5);
console.log(typeof num5);//输出 string
```
###### 数据类型转换

1. **转换为字符型**
1) 变量名.toString
```js
var num = 10;
var str = num.toString();
console.log(str);
console.log(typeof str);
```
2) String(变量名)
```js
console.log(String(num6));
```
3) **用 + 拼接 隐式转换**

2. **转换为数字型**
1) parseInt(变量) 可以把字符型转化为数字型 得到的是整数 不是四舍五入
```js
var age1 = prompt('请输入你的年龄');
console.log(parseInt(age));
        
console.log(parseInt('3.14'));//输出 3
console.log(parseInt('3.94'));//输出 3
console.log(parseInt('100px'));//输出 100 做动画会遇到
```
2)  parseFloat(变量) 可以把字符型转化为数字型 得到小数、浮点数
基本用法与 parseInt 一致
```js
console.log(parseFloat('3.14'));
```
3) Number
4) 隐式转换 - * /