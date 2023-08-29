# javascrpit面试题

## 1.什么是事件冒泡机制，具体是怎么作用的？

> 事件冒泡机制指的是当一个元素的事件被触发时，会逐层向上触发其他上层元素的事件，直到最顶层，即文档根元素。
>
> 作用：
>
> 1. 事件委托：可以将事件处理绑定在祖先元素上，而**不需要在每个子元素都绑定事件**，从而**降低内存占用**，同时还能实现一组**相关元素的事件统一处理**

## 2.null和undefined的区别

> - 数据类型不同（typeof可以判断）
>
> - 意义不同：undefined->变量未赋值
>                     null->变量赋值为空
>
> - 转数字结果不同
>
>   ​                 Number(undefined)=>NaN
>
>   ​				null => 0
>
> - 产生场景不同
>
>   ​		null: 使用原生js获取元素的方法，获取dom上没有的元素
>
>   ​		undefined: 声明变量未赋值，数组/对象没有某个属性，函数没有返回值，没有传递参数且没有设置默认参数

## 3.如何实现一个对象深拷贝

```javascript
function deepclone(obj) {
    // 判断对象是不是基础类型,是则直接返回
    if (typeof(obj) !== 'object' || obj!= null) {
        return obj
    }
    // d
    if (obj instanceof Array) {
        
    }
}
```

## 4.防抖，节流手写

```javascript
// 防抖
function debounce(fn, delay=1000) {
    let timer = null
    return function(){
		if (timer) {
         	clearTimeout(timer)
        }
        timer = setTimeout(fn,delay)
    }
}

// 节流
function throttle(fn, wait=1000) {
    let pre = Date.now()
    return function() {
        const now = Date.now()
        if (now-pre>wait) {
            fn()
            pre = Date.now()
        }
    }
}
```



## 5.数组去重的方法

## 6.js导致内存泄漏的操作有哪些？

## 7.什么是原型？

## 8.new操作符做了一件什么事情？

> 1. 隐式创建一个空对象
> 2. 将构造函数中的this指向这个空对象
> 3. 执行构造函数
> 4. 返回新对象

## 9.ES6新增哪些特性

> 1. 

## 10.如何判断两个对象是否相等

> 1.使用Object.keys()和Object.values()递归判断两个对象的属性及属性值是否完全相等
>
> ```javascript
>  const obj1 = {
>     a: 1,
>     c: 3,
>     b: 2
>   }
>   
>   const obj2 = {
>     a: 1,
>     b: 2,
>     c: 3
>   }
>   
>   function isEqual(obj1, obj2) {
>       const arr1 = Object.keys(obj1)
>       const arr2 = Object.keys(obj2)
>       if (arr1.length !== arr2.length ) return false
>       for (let k in obj1) {
>           if (typeof obj1[k] == 'object' || typeof obj2[k] == 'objcet') {
>               if (!isEqual(obj1[k], obj2[k])) return false
>           } else if (obj1[k] !== obj2[k]) return false
>       }
>       return true
>   }
> ```
>
> 

## 11.判断数据类型的方法

> 1.typeof：用于判断基本数据类型
>
> 2.instance of : 用于判断复杂数据类型
>
> 3.object.prototype.toString.call()或object.prototype.toString.apply()
>
> 让toString()的this指向当前检测的变量

## 12.创建对象的方法

> 1. 构造函数
> 2. 字面量
> 3. 自定义构造函数

## 13.创建函数的方式

> 1. 函数声明
> 2. 函数表达式
> 3. 构造函数

## 14.讲一下js有哪些常用的内置对象及其方法

> Math：floor,ceil,round,random,abs
>
> Number: isInterger
>
> Object: keys,values,assign
>
> Array: push,pop,shift,unshift,sort,splice,slice,reverse,foreach,map,filter,join,find,findIndexOf,indexOf,includes,slice,concat
>
> String:
>
> subString, substr, replace, split, slice, includes, indexOf,
>
> toLowerCase, toUpperCase
>
> Date:
>
> getFullYear,getMonth,getDate,getDay,getHours
>
> Function:
>
> call,apply,prototype,arguments

## 15.== 和 === 区别

> 1. == 会进行隐式类型转换，转为相同类型后再进行比较
> 2.  === 是严格等于，两边必须类型相等且值相等

## 16.如何区分数组和对象

> 1. Array内置方法: Array.isArray()
> 2. instanceOf
> 3. constructor
> 4. Object.prototype.call (apply)

## 17.多维数组降重

```javascript
const arr = [[222, 333, 444], [55, 66, 77]];

// join split
arr.join().split(',')

// flat
arr.flat(Infinity)

// 扩展运算符
const newArr = []
arr.foreach((item)=>{
    Array.isArray(item)? newArr.push(...item):newArr.push(item)
})

// concat
const newArr = []
arr.foreach((item)=>{
    Array.isArray(item)? newArr.concat(item):newArr.push(item)
})


// 递归
```

## 18.列举强制类型转换和隐式类型转换

> **强制类型转换**：
>
> - 转数字 Number parseInt parseFloat
> - 转字符串 String() toString()
> - 转布尔值 Boolean()
>
> **隐式类型转换**
>
> - 运算符

## 19.let const var区别

> **let/const**
>
> 1. es6新增
> 2. 具有块级作用域
> 3. 必须先声明后使用
> 4. 不能重复声明
> 5. 不存在变量提升
>
> **var**
>
> 1. 遵从函数作用域
> 2. 可以先使用后声明
> 3. 可以重复声明

## 20.for in for of 的区别

> for-in：
>
> - 适用：对象、数组、伪数组、字符串
> - 遍历当前对象可枚举属性及其原型链上的属性
> - 遍历的是属性或索引
> - 得到的索引是字符型
>
> for-of：
>
> - 适用：数组、伪数组、字符串
> - 遍历的是（可迭代的数据）数组 / 伪数组的元素、字符串的值
> - 得到的索引是数字型

## 21.具名函数和匿名函数的区别

> 具名函数：
>
> - 可以先声明后使用
> - 不能作为事件处理函数
> - 可以作用于构造函数
>
> 匿名函数
>
> - 必须先声明后使用
> - 可以作为事件处理函数
> - 不能作为构造函数

## 22.手写冒泡排序

```javascript

```











