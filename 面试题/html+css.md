# html+css面试题

## 1.什么是BFC?如何触发？有何特点？

> BFC就是块级格式化上下文，是css一种渲染机制
>
> **触发点**：
>
> 1. ​	float不为none时，会创建一个BFC，浮动元素就会脱离文档流
> 2. display： inline-block; inline-table; table-cell
> 3. position: absolute; fixed;
> 4. overflow : hidden; scroll ; auto;
>
> **特点**：
>
> 1. **内部元素垂直排列**：BFC 内部的块级元素会在垂直方向上一个接一个地排列，不会发生浮动或 margin 坍塌。
> 2. **内部元素不会影响外部元素**：BFC 内部的元素不会影响外部元素的布局，即使浮动元素也不会撑开 BFC 的外部容器。
> 3. **BFC 阻止外部浮动的影响**：一个元素的 BFC 可以包含浮动元素，这些浮动元素不会影响到 BFC 的高度，避免了浮动元素溢出。
> 4. **BFC 可以阻止 margin 坍塌**：当一个元素创建了 BFC，它的上下 margin 不会和外部元素的 margin 产生坍塌
>
> **使用场景**：
>
> 1. ​	解决浮动元素造成的布局问题
> 2. ​    创建独立的渲染环境避免与外界元素产生影响
> 3. ​    解决margin坍塌

## 2.什么是margin坍塌？如何解决？

> - 当两个块级元素上下排列时，他们的margin不会简单地叠加，而是会取较大的那个值，会导致页面出现意外的间距
> - 解决办法：
>   1.  使用BFC
>   2.  使用padding代替margin
>   3.  使用空的容器元素，在两个块级元素之间添加一个带有padding或者border的空div
>   4.  使用border属性为元素设置一个透明的边框

## 3.css选择器有哪些？优先级？哪些属性可以继承？

## 4.对HTML语义化的理解

> 1. 利于seo
> 2. 对开发人员友好，提升代码可读性
> 3. 利于一些设备的解析（盲人阅读器）
> 4. 在页面样式丢失时展示清晰结构

## 5.H5新增特性

> 1. canvas
> 2. 语义化标签：header,nav,aside,article,session
> 3. 音视频标签：video,audio
> 4. 自定义属性 ： data-
> 5. 浏览器缓存： localstorage 和 sessionstorage

## 6.什么是重绘和重排（回流）？

> 重绘： 页面中的元素颜色，外观，背景更改，浏览器对改动的元素进行重新绘制
>
> 回流：页面中的元素位置，个数发生变化，页面将重新进行渲染
>
> 浏览器渲染步骤  回流->重绘

## 7.css画三角形

> 

## 8.垂直水平居中的方法

> 1. flex布局：
> 2. 

## 9.css让元素隐藏

> - display: none
>
> - opacity: 0
> - positon: absolute; top: -1000px;
> - visibility: hidden
> - (如果有重叠元素) z-index:-9999
> - overflow: hidden
>
> 

## 10.介绍一下css盒模型

> - 标准盒子模型：  width = content
> - 怪异盒子模型（ie盒子模型）:  width = content + padding + border

## 11.分别介绍一下position的每个值

## 12.href和src的区别？alt和title的区别？

## 13.float的应用场景？float带来哪些影响？

## 14.如何清除float？

## 15.css3新增了哪些特性？

## 16.创建带有id属性的dom元素有什么副作用？

## 17.双飞翼布局？

## 18.圣杯布局？

## 19.css性能优化方法？



























































































































































































  