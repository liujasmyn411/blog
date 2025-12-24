ES6 笔记
块级作用域​：指的是变量在代码块（{}包裹的区域）内有效，超出这个代码块就无法访问。
主要实现方式：
- let​ 声明变量
- const​ 声明常量
let 和 const 声明的变量没有变量提升，var 有变量提升
```es6
//let
var a = 2;
{
  let a = 3;
  console.log(a); // 3
}
console.log(a); // 2
```
```es6

```