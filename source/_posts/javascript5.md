---
title: js-作用域及对象
date: 2025-12-25
tags: js
excerpt: 本篇简单记录了全局作用域、局部作用域和预解析。介绍了三种创建对象的方法，并用 for in 遍历对象。
---
### what
代码名字在某个范围内起效果，可以减少命名冲突并提高程序的可靠性。
#### 全局作用域
全局：整个 script 标签或一个 js 文件，
#### 局部作用域 (函数作用域)
在函数内部 比如 var

### 预解析
函数提前，
```js
f1 ();
console.log(c);
console.log(b);
console.log(a);
function f1 () {
    var a = b = c = 9;
    console.log(a);
    console.log(b);
    console.log(c);
}
```
相当于以下：
```js
function f1 () {
    var a 
    a = b = c = 9; //a 局部变量，b=c=9 是全局变量
    console.log(a);
    console.log(b);
    console.log(c);
}
f1 ();
console.log(c);
console.log(b);
console.log(a);//9 9 9 9 9 报错
```

### 对象
在 JavaScript 中，对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、函数等。对象是由属性和方法组成的。
属性：事物的特征，在对象中用属性来表示 (常用名词)
方法：事物的行为，在对象中用方法来表示 (常用动词)
**变量与属性的区别**
都可以储存数据
变量：单独声明并赋值，使用时直接写变量名 单独存在
属性：在{}里不需要声明，直接写，调用属性有规定的调用方法
**函数与方法的区别**
都实现某种功能
函数单独声明，并且调用的，单独存在
方法 在对象里面 有调用方法
#### 创建并使用对象 
1. 利用对象字面量{}
键值对的形式，多个属性和方法之间用逗号隔开。
```js
var obj = {
    uname: 'liu',
    age: 22, // 属性
    sayHi: function () {
        console.log(hi); // 方法
    }
}
```
调用对象属性
```js
console.log(obj.uname);// . 理解为的
console.log(obj['uname']);// 第二种使用方法
```
调用对象方法
```js
obj.sayHi(); // 小括号
```
2. 利用 new Object
等号赋值，用分号结束，调用方法相同
```js
var obj = new Object();
obj.uname = 'Ll';
obj.age = 22;
obj.sayHi = function () {
    console.log('hello');
}
```

3. 利用构造函数
前面的两种方法一次只能构造一次对象，利用函数可以快速构造大量对象。
构造函数名**首字母大写**，不需要 return 就可以返回对象
```js
function Name(形参) {
    this.属性 = 值;
    this.方法 = function () {}
}
new 构造函数名 (实参);
```
示例：
```js
function Star(uname, age) {
    this.name = uname;
    this.age = age;
    this.sing = finction(song) {
        console.log(song);
    }
}
var ldh = new Star('刘德华', 10,);
console.log(ldh.name);
ldh.sing('one');
var zxy = new Star('张学友', 11,);
console.log(ldh.name);
zxy.sing('two');
```
#### 遍历对象-for in
循环 但遍历对象是无序的，用 for in。k 是变量，也可以写别的
```js
var obj = {
    name = 'liu',
    age = 1,
    sex = '男',
}
for (var k in obj) {
    console.log(k); // 输出属性名
    console.log(obj[k]); // 输出属性值
}
```