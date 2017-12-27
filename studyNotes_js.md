# JS学习笔记
**1、 函数中参数 parameters 和 arguments区别**

    函数的parameters是函数被定义是列出的参数，为形参(formal parameter)
    函数arguments是函数调用时的真实值;parameters是arguments初始化时的值.
[详情](https://developer.mozilla.org/en-US/docs/Glossary/Parameter)
**2、javascript中arguments对象**
   
    arguments 是一个对应于传递给函数的参数的类数组对象。
    arguments对象是所有（非箭头）函数中都可用的局部变量。你可以使用arguments对象在函数中引用函数的参数。此对象包含传递给函数的每个参数的条目，第一个条目的索引从0开始。例如，如果一个函数传递了三个参数，你可以以如下方式引用他们：
```
  arguments[0]
  arguments[1]
  arguments[2]
```
    arguments对象不是一个 Array 。它类似于Array，但除了长度之外没有任何Array属性.
[详情](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)
