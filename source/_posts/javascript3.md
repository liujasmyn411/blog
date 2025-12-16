---
title: js-流程控制
date: 2025-12-16
tags: js
---
### 流程控制
#### 顺序结构

#### 分支结构
根据不同的条件，执行代码多选一。

##### if 语句
基本结构如下，若 if 里的表达式为 true，则执行大括号里的语句，反之执行 if 后面的语句。
```js
if (条件表达式) {
    //执行语句
}
```

##### if-else 双分支
基本结构如下，若 if 里的表达式为 true，则执行语句 1，反之执行语句 2。
```js
if (条件表达式) {
    //执行语句 1
} else if {
    //执行语句 2
}
```
##### if-else if 多分支语句
基本结构如下：
```js
if (condition) {
    //语句 1
} else if (condition) {
    //语句 2
} else if (condition) {
    //语句 3
} else{
    //语句 4
}
```
##### 三元表达式
? :
基本结构如下，条件表达式为 true，输出表达式 1 的值，反之输出表达式 2 的值。
```js
条件表达式 ? 表达式1 : 表达式2
```

练习：补 0 案例，可以用来做倒计时
```js
var num10 = prompt('请你输入数字 0 到 59 之间')
num10 = parseInt(num10); // 将字符串转换为数字
if (num10 < 10) {
    console.log("0" + num10);
} else {
    console.log(num10);
}
```
或者
```js
var num10 = prompt('请你输入数字 0 到 59 之间');
var time = num10 < 10 ? "0" + num10 : num10;
alert(time)
```
##### swith 语句
针对变量设置一系列特定值 
```js
switch (key) {
    case value://cash 例子或选项
    //执行语句 1
        break;//退出
//...还可以写 case
    default:
        break;
}
```

#### 循环结构
