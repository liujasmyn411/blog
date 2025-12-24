---
title: js-数组与函数
date: 2025-12-20
tags: js
---
### 数组的概念
之前所学的变量一次只能存储一个值，但是数组可以把一组相关的数据一起存放，并提供方便的访问方式。
数组是一组数的集合。
#### 数组的创建
1. 利用 new 创建数组
```js
var 数组名 = new Array();
```
2. 利用数组字面量创建数组[]
```js
var = [1, 2, 'Reno', ture];
```
#### 数组的索引
数组名[索引号]，索引号从 0 开始。
```js
var arr = [1, 2 , 'Reno' , true];
console.log(arr[1]);
```
**遍历数组**
利用循环，i 从 0 开始
```js
var arr = [1, 2 , 'Reno' , true];
console.log(arr[1]);
for (var i = 0; i < 3; i++){
    console.log(arr[i]);     
}
```

#### 数组的长度
length
```js
var arr = [1, 2 , 'Reno' , true];
console.log(arr.length); 
for (var i = 0; i < arr.length; i++){
    console.log(arr[i]);     
}
```
#### 找数组中的 max 值
```js
var arr = [1, 2 , 3 , 66];
var max = arr[0];
for (var i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
                max = arr[i];
    }
}
console.log('最大值' + max);
```
#### 数组中新增或替换元素
1. 修改 length 长度
2. 修改索引号
```js
var arr = [1, 2 , 'Reno' , true];
arr[4] = 'haha';
console.log(arr);  //新增
arr[2] = 'ha';
console.log(arr);  //替换
```

### 函数的概念
#### 1
封装了可以被重复执行的代码块：function
```js
function sayhi(函数名){
    函数体;//声明函数
}
sayhi();//必须调用函数
```
#### 函数参数

形参和实参
```js
function sayhi(形参1，形参2){

}
sayhi(实参1...);
```
例子
```js
function sayhi(aru){//形参是接受实参的，aru = '你好'，形参类似一个变量
    console.log(aru); 
}
sayhi('你好');
sayhi('hello');
```
形参和实参个数可以不匹配：实参大于形参，按顺序取到形参个数，实参小于形参，多余的形参定义为 undefined，最终输出结果 NaN

#### 函数返回值-return
把函数的最终结果返回给函数调用者，函数名 () = return 后面的结果 
```js
function get(num1,num2){
    return num + num2; 
}
console.log(get(1,2)); 
```

#### arguments
当不确定有多少参数传递的时候，可以用 arguments 来获取，arguments 对象中存储了传递的所有实参。