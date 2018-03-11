# JS object
Object构造函数为给定值创建一个对象包装器.
**Object构造函数的属性：**
(1) Object.prototype,可以为所有 Object 类型的对象添加属性.

## Object构造函数的方法
(1) Object.assign() :通过复制一个或多个对象来创建一个新的对象
(2) Object.create() :使用指定的原型对象和属性创建一个新对象
(3) Object.defineProperty() :给对象添加一个属性并指定该属性的配置.
(4) Object.defineProperties():给对象添加多个属性并分别指定它们的配置.
(5) Object.entries() :返回给定对象自身可枚举属性的[key, value]数组.
(6) Object.freeze() :冻结对象：其他代码不能删除或更改任何属性.
(7) Object.getOwnPropertyDescriptor() :返回对象指定的属性配置.
(8) Object.getOwnPropertyNames() :返回一个数组，它包含了指定对象所有的可枚举
    或不可枚举的属性名.
(9) Object.getOwnPropertySymbols() : 返回一个数组，它包含了指定对象自身所有的符号属性.
(10) Object.getPrototypeOf() :返回指定对象的原型对象
(11) Object.is() 比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）
(12) Object.isExtensible() 判断对象是否可扩展
(13) Object.isFrozen() 判断对象是否已经冻结
(14) Object.isSealed() 判断对象是否已经密封
(15) Object.keys() 返回一个包含所有给定对象自身可枚举属性名称的数组
(16) Object.preventExtensions() 防止对象的任何扩展
(17) Object.seal() 防止其他代码删除对象的属性
(18) Object.setPrototypeOf() 设置对象的原型（即内部[[Prototype]]属性
(19) Object.values() 返回给定对象自身可枚举值的数组.

## Object 实例和Object原型对象方法：
(1) [属性]Object.prototype.constructor 特定的函数，用于创建一个对象的原型
(2) Object.prototype.hasOwnProperty() 返回一个布尔值 ，表示某个对象是否含有指定的属性，
    而且此属性非原型链继承的
(3) Object.prototype.isPrototypeOf() 返回一个布尔值，表示指定的对象是否在本对象的原型链中
(4) Object.prototype.propertyIsEnumerable(),判断指定属性是否可枚举
(5) Object.prototype.toString(),返回对象的字符串表示
(6) Object.prototype.valueOf(),返回指定对象的原始值
