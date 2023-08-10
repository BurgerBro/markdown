# javascrpit面试题

1. 什么是事件冒泡机制，具体是怎么作用的？

2.  如何实现一个对象深拷贝

   ```javascript
   
   ```

   

3. 防抖，节流手写

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
   
   // 节流r
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

   

2. 数组去重的方法



