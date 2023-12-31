# Vue面试题

## 1.vue3的composition Api跟 options API 有什么区别，有什么优势

> optionsApi通过组件选项中定义data,methods,computed,watch等属性来组织组件的逻辑和状态，而composition Api通过使用setup函数将状态方法计算属性等逻辑组织在一起让代码更容易复用
>
> 优势：
>
> 1. composition Api可以将关联的逻辑组织在一起，不需要分散在各个选项
> 2. 更方便各组件之间进行逻辑复用

## 2.vue最大的优势是什么？

> 1. 中文教程上手简单
> 2. 许多方便快捷的操作，数据双向绑定，数据驱动视图，虚拟dom，组件化
> 3. 单页面应用，可以使页面局部刷新，不用每次跳转页面都请求所有数据和dom，加快访问速度和提升用户体验
> 4. 生态丰富，第三方ui库提高开发效率

## 3.mvc和mvvm的区别？

> MVC：也是一种设计模式，是Model数据模型，View试图，Controller控制器，在控制器这层里面编写js代码，来控制数据和视图关联，MVC是单向通信；
>
> MVVM：既 `Model-View-ViewModel`的简写，模型-视图-视图模型，VM是整个设计模式的核心，有两个方向，首先：模型转换为视图，将从后端请求回来的数据转化为网页，实现方式：数据绑定；其次：视图转换为模型，将网页转化为后端的数据，实现方式：监听DOM时间。这两个方向都是先了，我们就成为数据的双向绑定；
>
> 区别：都是一种设计思想，主要就是MVC中的Controller演变成MVVM中的VM。MVVM主要解决了MVC中大量的DOM操作导致的页面渲染性能低，加载速度慢，影响用户体验。

## 4.vue有哪些常用修饰符

> 1. 事件修饰符
>
>    .stop 阻止事件冒泡
>    .prevent 阻止默认事件
>    .once 事件处理函数只执行一次
>    .native 原生事件
>
> 2. 按键修饰符
>
>    .enter 监听enter键
>    .esc 监听esc键
>
> 3. v-model修饰符
>
>    .number 尝试用parseFloat转数
>
>    .trim 去处字符串两侧的空白
>
>    .lazy 内容改变并且失去焦点触发

## 5.v-for和v-if为什么不能在一起使用

> v-for 的优先级比 v-if要高，会造成性能损耗，如果n次循环则执行n次v-if，解决办法template标签实现父子关系嵌套，子层使用v-for

## 6.有时数组更新v-for不渲染原因

> vue内部只检测数组的顺序，位置，数量
>
> 如何数组中的某个值被重新赋值，或使用了不改变数组的方法，vue无法检测到
>
> 针对这一点，两种解决方案：
>
> 1. 重新赋值，使用this.$set
> 2. 使用不改变数组的方法，用得到的新数组替换原来的旧数组

## 7.为什么vue中不能用索引作为key

> 在 Vue 中，`key` 是用于标识 Vue 的虚拟 DOM 中的节点的唯一性的属性。当 Vue 更新视图时，它会使用 `key` 来识别哪些节点需要更新、删除或重新渲染，以保持视图和数据的同步。
>
> 使用索引作为 `key` 可能会引发一些问题，尤其是在动态数据变化的情况下。如果你使用索引作为 `key`，当数组中的元素发生变化，例如插入、删除或重新排序，索引可能会改变，导致 Vue 不正确地更新视图。

## 8.vue组件之间如何进行通信

> 父子组件：
> 	props和$emit进行通信
>     $parent, $children
>     $refs
>     Provide/Inject
>
> 兄弟组件
> 	$parent, $children
> 	eventbus
> 	localstorage/sessionstorage
> 	vuex

## 9.mvc和mvvm的区别

> mvc和mvvm都是一种设计思想，有助于将程序结构设计的更加清晰，降低耦合度，提高重用性。
>
> 他们之间最大的区别在于mvvm实现了view和model之间的自动同步
>
> - 当model改变时不用手动操作dom去改变view的显示，view的显示会自动改变
>
> **阐述一下你所理解的MVVM响应式原理**
>
> - vue是采用数据劫持配合发布者-订阅者的模式的方式，
>   - 通过**Object.defineProperty()来劫持各个属性的getter和setter**，
>   - 在数据变动时，发布消息给依赖收集器（dep中的subs），去通知（notify）观察者，做出对应的回调函数，更新视图
> - MVVM作为绑定的入口，整合Observer,Compile和Watcher三者，
>   - 通过Observer来监听model数据变化，
>   - 通过Compile来解析编译模板指令，
>   - 最终利用Watcher搭起Observer，Compile之间的通信桥路，
>   - 达到**数据变化Observer）=>视图更新**；**视图交互变化=>数据model变更**的双向绑定效果。













