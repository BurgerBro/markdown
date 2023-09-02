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

> 1. foreach+indexof
> 2. foreach+find
> 3. foreach+includes
> 4. foreach+sort+splice
> 5. filter+indexof
> 6. Array.from + set

## 6.js导致内存泄漏的操作有哪些？

## 7.什么是原型？

## 8.new操作符做了一件什么事情？

> 1. 隐式创建一个空对象
> 2. 将构造函数中的this指向这个空对象
> 3. 执行构造函数
> 4. 返回新对象

## 9.ES6新增哪些特性

> 1. let,const
> 2. 扩展运算符
> 3. 解构赋值
> 4. 箭头函数
> 5. 函数参数默认值
> 6. 模板字符串
> 7. map,set
> 8. 模块导入导出（import）
> 9. promise
> 10. 数组方法（splice,sort,foreach,map,filter,reduce,some,every,join,find,concat,reverse)
> 11. 字符串方法
>     （substring,startswith,endswith,split,includes,replace)

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
let arr = [1,3,2]
for (let i = 0; i<arr.length-1; i++) {
    for (let j = 0; j<arr.length-i-1; j++) {
        if (arr[j]>arr[j+1]) {
            [arr[j],arr[j+1]] = [arr[j+1],arr[j]]
        }
    }
}
```

## 23.数组和伪数组的区别

> 1. 共同点：可以通过索引取值，都有length属性
> 2. 区别：原型不同

## 24.dom常用操作

> 1. 创建节点：document.createElement()
> 2. crud: 
>    添加：appendChild()
>    移除：removeChild()
>    替换：repalceChild()
>    插入：insertBefore()
> 3. 查找节点
>    父节点：parentNode()
>    子节点：children (伪数组)

## 25.js定时器有哪些？

> 1. setTimeout ： 单次定时器，使用clearTimeout清除
> 2. setInterval : 无限循环 ，使用clearInterval清除

## 26.js动画与css动画区别

> JS动画：
>
> - 优点：
>   - JS动画控制能力强，可以在动画播放过程中对动画进行控制：开始、暂停、回放、停止、取消等
>   - 动画效果比C3动画更丰富（曲线运动、视差滚动）
>   - C3动画有兼容性，而JS动画大多时候没有兼容性问题
> - 缺点：
>   - 代码的复杂程度高于C3动画
>   - JS在浏览器主线程中运行，而主线程中还有其他需要运行的JS脚本、样式计算、布局、绘制任务等，对其他干扰导致线程可能出现阻塞，从而造成丢帧的情况
>
> C3动画：
>
> - 优点：
>   - 浏览器可对动画进行优化
>   - 代码相对简单，性能调优方向固定
>   - 相对帧速表现不好的低版本浏览器，C3可以自动降级，而JS需要撰写额外代码
> - 缺点：
>   - 运行过程控制较弱，无法附加事件绑定回调函数
>   - 代码冗长。实现复杂的动画，CSS代码就会变得非常笨重
>
> C3和JS动画差异：
>
> - 代码复杂程度，JS动画代码相对复杂一些
> - 动画运行时，对动画的控制程度上，JS能够让动画暂停、取消、终止，CSS动画不能添加事件
> - 动画性能看，JS动画多了一个JS解析的过程，解析功能不如C3动画好
> - 总结：
>   - 简单的状态切换，不需要中间过程控制，C3动画是优选方案
>   - 复杂的动画，应该使用JS动画去实现

## 27.浏览器渲染的过程，dom树与渲染树的区别

> 1.渲染过程：解析html成为dom树，并请求css,js,img等资源文件，css文件下载完成后开始构建css树，css树构建完成后与dom树一起生成渲染树
>
> 2.DOM树和渲染树的区别： 1）DOM树与HTML标签一一对应，包括head和隐藏元素 2）渲染树不包括head和隐藏元素，大段文本的每一个行都是独立节点，每一个节点都有对应的css属性

## 28.如何最小化回流和重绘

> 回流: 当页面中元素的位置，个数，大小，布局发生变化时触发
>
> 重绘：页面中元素的色彩等属性发生变化但不引起布局改变，只改变外观
>
> 最小化方法：
>
> 1. 需要对元素进行复杂操作时可以先隐藏操作完再显示
> 2. 需要创建多个dom节点时，可以先创建多个后一次性添加
> 3. 尽量使用css属性简写
> 4. 批量修改元素样式（使用新增类名和移除类名的犯法）

## 29.合并数组有哪些方法

> 1. concat
> 2. push+扩展运算符
> 3. []+扩展运算符

## 30.如何终止foreach

> 错误用法：break（会报错）、return（只是终止本次循环）
>
> forEach专门用来循环数组，可以直接取到元素，同时也可以取到index的值，存在局限性，不能continue跳过或者break终止循环，没有返回值，不能return
>
> 终止forEach循环：运用抛出异常（try-catch）可以终止forEach循环

## 31.解释一下什么是作用域链

> 作用域指的是变量能够被访问到的范围
>
> 嵌套的作用域形成了作用域链
>
> 作用域链的作用就是当函数执行时会先在当前作用域查找变量，若无，则会在其作用域链逐层向上寻找

## 32.解释一下什么是闭包

> 内层函数使用了外层函数的变量就会出现闭包
>
> 作用：实现变量私有化，延长变量作用范围
>
> 缺点：导致内存泄漏

## 33.什么是内存泄漏，哪些操作会导致内存泄漏

> 1. 内存泄漏指的是不再使用的内存没有被及时回收，导致一直占用空间，系统失去对一段内存空间的控制
> 2. 导致内存泄露的操作：闭包，setTimeout第一个参数为字符串，对象循环引用，console.log

## 34.什么是垃圾回收机制？有哪些方法？

> js中内存的分配和回收都是自动的，当内存不再使用时会被垃圾回收器自动回收
>
> 标记清除法，引用计数法

## 35.什么是js预解析

> 变量的声明提升：
>
> - 在代码执行之前，检测在当前作用域下所有用var声明的变量，并将这些变量的声明提升到当前作用域的最前面
> - 注意：只提升声明，不提升赋值
>
> 函数的声明提升：
>
> - 代码执行之前，会将所有函数声明提升到当前作用域的最前面
> - 注意：
>   - 只提升声明，不提升调用
>   - 函数表达式不存在函数提升（必须先声明后调用）
>
> 函数提升优先级高于变量提升

## 35.箭头函数与普通函数的区别

> 1. 箭头函数没有function关键字
> 2. 箭头函数没有arguments动态参数
> 3. 箭头函数没有this
> 4. 箭头函数不能是构造函数
> 5. 箭头函数替代了原本需要匿名函数的地方

## 36.说说对原型的理解

> 每一个构造函数都有一个原型对象，prototype,这个对象可以添加属性及挂载函数以实现继承和扩展对象

## 37.讲讲原型链

> 当访问一个对象的某个属性时，会先在自身查找，找不到时会在其原型链上查找（实例的\_proto\_指向的prototype),原型没有在原型的原型上查找，一直到null为止

## 38.js继承方式有哪些

> 1. **原型链继承**： 通过让一个构造函数的原型对象指向另一个构造函数的实例，从而实现继承。但是原型链继承有一些问题，比如属性共享和无法传递参数给父类构造函数。
>
>    ```js
>    javascriptCopy codefunction Parent() {
>      this.name = 'Parent';
>    }
>    
>    Parent.prototype.sayHello = function() {
>      console.log(`Hello from ${this.name}`);
>    }
>    
>    function Child() {}
>    
>    Child.prototype = new Parent();
>    
>    const child = new Child();
>    child.sayHello(); // Output: "Hello from Parent"
>    ```
>
> 2. **构造函数继承**： 在子类构造函数中调用父类构造函数，可以通过使用 `call` 或 `apply` 方法来实现。这种方式可以解决原型链继承中的属性共享问题，但无法继承父类原型上的方法。
>
>    ```js
>    javascriptCopy codefunction Parent(name) {
>      this.name = name;
>    }
>    
>    function Child(name) {
>      Parent.call(this, name);
>    }
>    
>    const child = new Child('Child');
>    console.log(child.name); // Output: "Child"
>    ```
>
> 3. **组合继承**： 结合原型链继承和构造函数继承，通过调用父类构造函数并设置子类的原型为父类实例，可以继承父类构造函数的属性并保留原型链上的方法。
>
>    ```js
>    javascriptCopy codefunction Parent(name) {
>      this.name = name;
>    }
>    
>    Parent.prototype.sayHello = function() {
>      console.log(`Hello from ${this.name}`);
>    }
>    
>    function Child(name) {
>      Parent.call(this, name);
>    }
>    
>    Child.prototype = new Parent();
>    
>    const child = new Child('Child');
>    child.sayHello(); // Output: "Hello from Child"
>    ```
>
> 4. **原型式继承**： 借助一个临时构造函数，通过设置其原型为父类实例来实现继承。这种方式类似于原型链继承，也存在属性共享的问题。
>
>    ```js
>    javascriptCopy codefunction createInheritedObject(parent) {
>      function F() {}
>      F.prototype = parent;
>      return new F();
>    }
>    
>    const parent = {
>      name: 'Parent',
>      sayHello: function() {
>        console.log(`Hello from ${this.name}`);
>      }
>    };
>    
>    const child = createInheritedObject(parent);
>    child.name = 'Child';
>    child.sayHello(); // Output: "Hello from Child"
>    ```
>
> 5. **寄生式继承**： 在原型式继承的基础上，增强对象，可以在继承的基础上添加额外的属性或方法。
>
>    ```js
>    javascriptCopy codefunction createInheritedObjectWithExtras(parent, extraProps) {
>      const child = createInheritedObject(parent);
>      Object.assign(child, extraProps);
>      return child;
>    }
>    
>    const parent = {
>      name: 'Parent',
>      sayHello: function() {
>        console.log(`Hello from ${this.name}`);
>      }
>    };
>    
>    const child = createInheritedObjectWithExtras(parent, { age: 10 });
>    console.log(child.age); // Output: 10
>    ```
>
> 6. **ES6 Class继承**： 使用 ES6 的 `class` 关键字和 `extends` 关键字可以更方便地实现继承。
>
>    ```javascript
>    javascriptCopy codeclass Parent {
>      constructor(name) {
>        this.name = name;
>      }
>       
>      sayHello() {
>        console.log(`Hello from ${this.name}`);
>      }
>    }
>       
>    class Child extends Parent {
>      constructor(name) {
>        super(name);
>      }
>    }
>       
>    const child = new Child('Child');
>    child.sayHello(); // Output: "Hello from Child"
>    ```

## 39.各种情况下this的指向

> 1. 普通函数，谁调用指向谁
> 2. 调用者不明确指向window
> 3. 构造函数及原型中指向实例对象
> 4. 箭头函数没有自己的this，沿用他创建环境的this

## 40.call，apply，bind的区别

> 1. 共同点：都是改变this指向，第一个参数都是this指向的对象，后续参数用于传参
>
> 2. 不同点：
>    call,bind后续参数是接收多个参数
>    apply是接收一个参数数组
>
>    bind会返回一个新函数已经修改好this指向的函数

## 41.什么是事件循环机制

> js执行代码时将任务分为同步任务列和异步任务列，浏览器执行主线程会先将同步任务队列执行完毕后， 再去执行异步任务队列，异步任务队列又分为宏任务队列和微任务队列，微任务队列的优先级是高于宏任务队列的，主线程会先执行完微任务后再去执行宏任务，当执行宏任务的过程中没执行完一个宏任务都会去检查是否有微任务需要执行，若有则先执行微任务再执行宏任务

## 42.常见的宏任务，微任务

> 1. 宏任务：ajax，定时器，文件操作
> 2. 微任务：promise,process.nexttick

## 43.如何实现一个对象的拷贝

> 拷贝分别深拷贝和浅拷贝
>
> 浅拷贝：拷贝栈中的地址
> 	实现方法：扩展运算符，objcet.assign(),直接赋值
>
> 深拷贝：拷贝堆中的数据
> 	实现方法：创建空对象递归属性赋值，属性值为数组或对象时，赋值为空数组或空对象继续递归，基本类型则直接赋值；json.stringfy() + json.parse()

## 44.构造函数与普通函数的区别

> 1. this指向不同
>    构造函数指向实例
>    普通函数指向调用者
>
> 2. 调用方式不同
>
>    构造函数使用new操作符
>
>    普通函数直接函数名加括号
>
> 3. 函数名不同
>    构造函数大驼峰
>    普通函数小驼峰
>
> 4. 构造函数不能是箭头函数，可以实现继承

## 45.js作用域有哪些

> 作用域 = 全局作用域+局部作用域 = 块级作用域 + 函数作用域

## 46.cooklie,sessionstorage,localstorage的区别

> `cookie`：是网站为了标识用户身份而存储在本地终端上的数据（通常是经过加密）
>
> - 如果不给cookie设置过期时间，则表示这个Cookie生命周期为浏览器会话期间，只要关闭浏览器窗口，Cookie就消失了
>
> `cookie`数据始终在同源http请求中携带（也就是说cookie在浏览器和服务器之间来回传递）而`sessionStorage`和`localStorage`不会主动把报数据发送给服务器
>
> 存储大小限制不同：
>
> - `cookie`：不能超过`4KB`
> - `sessionStorage + localStorage`：虽然也有存储大小限制，但相比cookie要打得到，可以达到`5M`甚至更大
>
> 数据的有效期不同：
>
> - `cookie`：只在设置的过期时效之前一直有效，及时关闭页面或浏览器
> - `sessionStorage`：尽在当前页面没有关闭之前有效
> - `localStorage`：始终有效，窗口或浏览器关闭也是有效的，除非手动清除
>
> 作用域不同：
>
> - `cookie`：在所有同源窗口中都是共享的
> - `sessionStorage`：只在当前窗口中共享
> - `localStorage`：在所有同源窗口中是共享的
>
> cookie并把真都能通过js获取，如果设置了httponly，是获取不到的

## 47.CommonJS 和 ES6模块化的区别？

> CommonJS是同步加载，ES6模块化是异步加载
>
> CommonJS模块输出的是一个值的拷贝，ES6模块输出的是值的引用
>
> 1）CommonJS：一旦输出一个值，模块内部的变化就影响不到这个值
>
> 2）ES6：JS引擎对脚本静态分析的时候，遇到模块加载命令import，就会生成一个只读引用。等到脚本真正执行时，再根据这个只读引用，到被加载的那个模块里面去取值
>
> CommonJS模块是运行时加载，ES6模块是编译时输出接口
>
> 1）CommonJS加载的是一个对象，该对象只有在脚本运行完才会生成
>
> 2）ES6模块不是对象，它的对外接口只是一种静态定义，在代码静态解析阶段就会生成





















