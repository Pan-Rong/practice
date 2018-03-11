## ES6练习题

(1)数组的结构
```
function* fibs() {
  let a = 0;
  let b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

let [first, second, third, fourth, fifth, sixth] = fibs();
first //1
second //1
third  //1
fourth //2
fifth  //3
sixth // 5
```
***注：***
有上述结果可知，`[a, b] = [b,a + b]`右边的计算，是针对上一次的状态，和本次计算的结果无关。

变量的解构，默认值生效的条件是，对象的属性值***严格***等于undefined.
例：
```
var {x=3} = {x:undefined};
x //3
var {x=3} = {x:null};
x //null
```

(2)函数参数的解构也可以使用默认值
例：
```
function move({x = 0, y = 0} = {}) {
  return [x, y];
}
move({x: 3, y: 8}); // [3, 8]
move({x: 3}); // [3, 0]
move({}); // [0, 0]
move(); // [0, 0]
```
下面的示例，结果就不一样了：
```
function move({x, y} = { x: 0, y: 0 }) {
  return [x, y];
}
move({x: 3, y: 8}); // [3, 8]
move({x: 3}); // [3, undefined]
move({}); // [undefined, undefined]
move(); // [0, 0]
```
## 变量的解构赋值用途：
(1) 交换变量的值
(2) 从函数返回多个值
(3) 函数参数的定义
(4) 提取 JSON 数据
```
let jsonData = {
  id: 42,
  status: "OK",
  data: [867, 5309]
};
let { id, status, data: number } = jsonData;
console.log(id, status, number);
// 42, "OK", [867, 5309]
```
(5) 函数参数的默认值
(6) 遍历Map结构
```
const map = new Map();
map.set('first', 'hello');
map.set('second', 'world');

for (let [key, value] of map) {
  console.log(key + " is " + value);
}
// first is hello
// second is world
```
(7) 输入模块的指定方法
```
const { SourceMapConsumer, SourceNode } = require("source-map");
```
