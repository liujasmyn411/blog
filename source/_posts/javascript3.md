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

### 循环结构
#### for 循环
初始化变量就是用 var 声明的一个普通变量，通常用于计数器使用；条件表达式是终止的条件；操作表达式是每次循环最后执行的代码，用于计数器变量进行递增或递减。

for 语法结构如下
```js
for (let index = 0; index < array.length; index++) {
    const element = array[index];
    
}
//输出 100 次你好呀 i++ 最后执行
for(var i = 1; i <= 100; i++){
    console.log('你好呀');
}
```
##### 断点调试
<img src="/blog//images/断点.png" title="断点调试" width="400px"/>

##### for 循环重复循环相同代码
```js
var num = prompt('输入循环的次数')
for(var i = 1; i <= num; i++){
    console.log('你好呀');
}
```
##### for 循环重复循环不相同代码
```js
for(var i = 1; i <= 100; i++){
    if (i==1) {
        console.log('年轻');
    }else if(i==100){
         console.log('老了');
    }else{
        console.log('你好呀');
    }   
}
```
##### for 循环重复相同算数运算操作
求 1~100 的相加的和 sum+i
```js
var sum = 0
for (var i =1; i <=100; i++){
    sum = sum + i
}
console.log(sum);
average = sum/100;
console.log(average);//求平均数
```
奇数和与偶数和
```js
var even = 0
    odd = 0
for (var i = 1; i <= 100; i++){
    if (i % 2 == 0) {
        even = even + i;
    } else {
        odd = odd + i;
    }
}
console.log('奇数和' + even);
console.log('偶数和' + odd);
```
用户输入一行打印 几 个星星，采取追加字符串的方式
```js
var num = prompt('请输入星星的个数');
var str = '';
for (var i = 1; i <= num; i++) {
    str = str + '☆';
}
console.log(str);
```
##### 双重 for 循环
循环嵌套 基本结构
```js
for(var i = 1; i <= 3; i++) {
    console.log('外循环' + i + '次');
        for(var j = 1; j <= 3; j++) {
        console.log('内循环' + j + '次');
        }
}
```
#### while 循环
基本结构：当条件表达式为 true 执行循环体，为假停止执行，也有计数器和技术表达式
```js
while (条件表达式) {
    //循环体
}

var num = 1;
    while (num <= 100) {
    console.log('你好');
    num++;
}
```
不输入正确答案就一直循环
```js
var message = prompt('一闪一闪');
while (message !== '亮晶晶') {
    message = prompt('一闪一闪');
}
alert('恭喜答对');
```
#### do while 循环
基本结构：先执行一次循环体再判断条件，条件表达式结果为真，继续循环，反之退出循环。
```js
do {
    // 循环体
}while(条件表达式)
```

#### continue 与 break
continue 跳出当前循环
breakk 跳出整个循环