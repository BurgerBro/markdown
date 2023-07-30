# JSX

> JSX是JavaScript 语法扩展，可以让你在JavaScript 文件中书写类似 HTML 的标签
> JSX浏览器是不认识的，所以利用脚手架中的SWC或Babel进行编译，转换成浏览器识别的代码JSX and React 是相互独立的东西。
>
> 但它们经常一起使用，但你可以单独使用它们中的任意一个，JSX 是一种语法扩展，而 React 则是一个JavaScript 的库

js 中的html标签中会转为一个虚拟dom对象，react-dom模块操作真实dom在浏览器中进行渲染

![image-20230729212730591](C:\Users\67573\AppData\Roaming\Typora\typora-user-images\image-20230729212730591.png)



## JSX语法与HTML的区别

> 1. 原生标签名需要全部写为小写
> 2. 标签必须要闭合，不能缩写
> 3. class 需要写为 className
> 4. for 需要写为 htmlfor 如 `<label forhtml='input></label>'`
> 5. 属性需要写为驼峰式命名（自定义属性除外，如 `data-id`）
> 6. 可以在{ }使用js，类似vue表达式
> 7. 属性使用变量要用{ }

## 样式

> - 行内样式需用`style={objet}`格式，object为一个样式对象

局部样式文件命名 **filename.module.css** 使用时需要在对应文件导入对象

> **实际问题**：当局部样式时某个css属性使用了-连接，要如何在jsx中书写

- 方法一 : `className = {style['class-name']}`

- 方法二：配置vite.config.js如下图后，即可直接使用驼峰式写法

  className = style.className

![image-20230730013724390](C:\Users\67573\AppData\Roaming\Typora\typora-user-images\image-20230730013724390.png)