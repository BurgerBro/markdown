# javascrpit面试题

## 1.什么是事件冒泡机制，具体是怎么作用的？

## 2.null和undefined的区别

> - 数据类型不同（typeof可以判断）

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

## 10.如何判断两个对象是否相等

