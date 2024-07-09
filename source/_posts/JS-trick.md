---
title: JS小技巧
tags:
  - JS
  - 小技巧
categories:
  - JS
date: 2024-06-27 00:00:00
---

>收录了一些关于JS的小技巧。

### 1. 获取元素宽高

```js  
document.getElementById('id').offsetWidth
document.getElementById('id').offsetHeight
// offsetWidth 和 offsetHeight 获取元素宽高，包含元素的边框 (border)、内边距 (padding)、滚动条 (scrollbar)（如果存在的话）、以及 CSS 设置的宽度 (width)/高度（height）的值。

document.getElementById('id').clientWidth
document.getElementById('id').clientHeight
// clientWidth 和 clientHeight 获取元素宽高，包含内边距，但不包括边框、外边距和滚动条（如果存在）。

document.getElementById('id').scrollWidth
document.getElementById('id').scrollHeight
// scrollWidth 和 scrollHeight 该元素在不使用滚动条的情况下为了适应视口中所用内容所需的最小宽度/高度，元素内容高度的度量，包括由于溢出导致的视图中不可见内容, 包括元素的内边距，但不包括元素的边框、外边距以及滚动条（如果存在）。 
```

![alt text](/images/JS-trick/image-1.png 'offsetWidth 和 offsetHeight')  
![alt text](/images/JS-trick/image-2.png 'clientWidth 和 clientHeight')  
![alt text](/images/JS-trick/image-3.png 'scrollWidth 和 scrollHeight')  

### 2. 获取元素位置

```js  
document.getElementById('id').offsetLeft
document.getElementById('id').offsetTop
// offsetLeft 和 offsetTop 获取元素相对于其 offsetParent 元素的左和上偏移量。

document.getElementById('id').clientLeft
document.getElementById('id').clientTop
// clientLeft 和 clientTop 获取元素相对于其 offsetParent 元素的左和上偏移量。

document.getElementById('id').scrollLeft
document.getElementById('id').scrollTop  
// scrollLeft 和 scrollTop 获取元素滚动条的位置。
```

### 3. 空值合并运算符（??）

空值合并运算符（??）是一个逻辑运算符，当左侧的操作数为 null 或者 undefined 时，返回其右侧操作数，否则返回左侧操作数。
与逻辑或运算符（||）不同，逻辑或运算符会在左侧操作数为假值时返回右侧操作数。也就是说，如果使用 ||来为某些变量设置默认值，可能会遇到意料之外的行为。比如为假值（例如，'' 或 0）时。

### 4. structuredClone  

structuredClone() 方法用于创建一个对象的深拷贝。支持循环引用。

```js
let obj = {
    a: 1,
    b: 2
};
obj.obj = obj;
const copy = structuredClone(obj);
```

### 5. ~~运算符取整  

~是按位取反运算，\~~是取反两次，在这里~~的作用是去掉小数部分。
因为位运算的操作值要求是整数，其结果也是整数，所以经过位运算的都会自动变成整数。  

```js
// 取整
Math.floor(Math.random() * 50);

// 取整
~~(Math.random() * 50);
~~'1.11111'; // 1
~~'string'; //  0
~~NaN; //  0
```

### 6. 灵活使用 array.length 调整数组长度或清空数组  

```js
const array = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'];

console.log(array.length); //  10

// 调整数组大小
array.length = 4;

console.log(array.length); //  4
console.log(array); // ['a', 'b', 'c', 'd']

// 清空数组
array.length = 0;
console.log(array.length); //  0
console.log(array); // []
```

### 7. 防抖与节流

>- 节流: n 秒内只运行一次，若在 n 秒内重复触发，只有一次生效。
>- 防抖: n 秒后再执行该事件，若在 n 秒内被重复触发，则重新计时。

精辟描述：防抖就是回城，节流就是放技能  

### 8. 判断对象是否为空

```js
const isEmptyObject = (object)=>{
    try {
        if (Reflect.ownKeys(object).length === 0) {
            console.log(`输入值是空对象`)
        } else {
            console.log(`输入值不是空对象`)
        }
    } catch {
        console.log(`输入值不是对象`)
    }
}
```
