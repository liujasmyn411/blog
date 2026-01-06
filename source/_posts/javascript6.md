---
title: js-内置对象
date: 2025-12-30
tags: js
excerpt: 
---
### Math
#### 构建自己的数学对象
```js
var Mymath = {
    PI: 3.14159,
    max: function() {
        var max = arguments[0];
        for (var i = 1; i < arguments.length; i++) {
        if (arguments[i] > max)  {
            max = arguments[i]
            };
        }
        return max
    },
    min: function() {
        var min = arguments[0];
        for (var i = 1; i < arguments.length; i++) {
        if (arguments[i] < min)  {
            min = arguments[i]
            };
        }
    return min
    }
} 
console.log(Mymath.PI);
console.log(Mymath.max(1, 10, 99));
console.log(Mymath.min(1, 10, 99));
```
#### random
```js
// 随机数
console.log(Math.random());
// 随机出整数
function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandom(1, 10));
//随机点名
var arr = ['张','李', '王', '刘'];
console.log(arr[getRandom(0, arr.length-1)]);
```

### 构造函数-Date

