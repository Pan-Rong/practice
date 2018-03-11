# JS中的Array
数组是一种类列表对象，它的原型中提供了遍历和修改元素的相关操作。JavaScript 数组的长度和元素类型都是非固定的

## 正则匹配结果所返回的数组
使用正则表达式匹配字符串可以得到一个数组,RegExp.exec、String.match、String.replace 都会返回这样的数组.

## Array方法
(1) Array.from() :从类数组对象或者可迭代对象中创建一个新的数组实例
(2) Array.isArray() :用来判断某个变量是否是一个数组对象.

## 数组实例的方法
以下这些方法会改变调用他们的对象自身的值：
(1) Array.prototype.pop():删除数组的最后一个元素，并返回这个元素
(2) Array.prototype.push():在数组的末尾增加一个或多个元素，并返回数组的新长度
(3) Array.prototype.reverse():颠倒数组中元素的排列顺序
(4) Array.prototype.shift():删除数组的第一个元素，并返回这个元素
(5) Array.prototype.sort():对数组元素进行排序，并返回当前数组
(6) Array.prototype.splice() :在任意的位置给数组添加或删除任意个元素
(7) Array.prototype.unshift(): 在数组的开头增加一个或多个元素，并返回数组的新长度

以下这些方法不会改变调用他们的对象值，只会返回一个新的数组或返回一个其他的期望值：
(1) Array.prototype.concat():返回一个由当前数组和其它若干个数组或者若干个非数组值组合而成的新数组
(2) Array.prototype.join():连接所有数组元素组成一个字符串
(3) Array.prototype.slice():抽取当前数组中的一段元素组合成一个新数组
(4) Array.prototype.toString():返回一个由所有数组元素组合而成的字符串.
(5) Array.prototype.indexOf():返回数组中第一个与指定值相等的元素的索引，如果找不到这样的元素，则返回 -1
(6) Array.prototype.lastIndexOf():返回数组中最后一个（从右边数第一个）与指定值相等的元素的索引，如果找
    不到这样的元素，则返回 -1.
    
以下是迭代方法：
(1) Array.prototype.forEach() :为数组中的每个元素执行一次回调函数
(2) Array.prototype.every():如果数组中的每个元素都满足测试函数，则返回 true，否则返回 false
(3) Array.prototype.some():如果数组中至少有一个元素满足测试函数，则返回 true，否则返回 false
(4) Array.prototype.filter():将所有在过滤函数中返回 true 的数组元素放进一个新数组中并返回
(5) Array.prototype.map():返回一个由回调函数的返回值组成的新数组
(6) Array.prototype.reduce():从左到右为每个数组元素执行一次回调函数，并把上次回调函数的返回值放在一个
    暂存器中传给下次回调函数，并返回最后一次回调函数的返回值

