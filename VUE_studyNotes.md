# VUE 学习笔记

## 一、定义：

> Vue是用于构建用户界面的渐进式框架，只关注视图层。

## 二、引入
 
+ 在.html中直接引入，示例代码：
```
  <!-- 开发环境版本，包含了用帮助的命令行警告 -->
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  
  <!-- 生产环境版本，优化了尺寸和速度 -->
  <script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

+ 使用Vue的脚手架`Vue-cli`;
```
npm install -g @vue/cli

vue create my-project

npm install vue

```

## 三、事件

+ 声明式渲染，示例：
```
//html
    <div id="app">
      {{ message }}
    </div>
//JS文件
    var app = new Vue({
      el: '#app',
      data: {
        message: 'Hello Vue!'
      }
    })
```
+ `v-bind`指令，指令带有前缀`v-`，以表示他们是Vue提供的特殊特性。
+ 条件与循环,用`v-if`,例
```
/*-------------if示例----"v-if"-------------------------*/
  //html
    <div id="app-3">
      <p v-if="seen">现在你看到我了</p>
    </div>
  //JS文件
  var app3 = new Vue({
      el: '#app-3',
      data: {
        seen: true
      }
    })
 /*-------------for示例---"v-for"--------------------------*/
  //html
    <div id="app-4">
      <ol>
        <li v-for="todo in todos">
          {{ todo.text }}
        </li>
      </ol>
    </div>
  //JS文件
  var app4 = new Vue({
    el: '#app-4',
    data: {
      todos: [
        { text: '学习 JavaScript' },
        { text: '学习 Vue' },
        { text: '整个牛项目' }
      ]
    }
  })
  //用 " app4.todos.push({ text: '新项目' })"可实现新增
```
+ 用户输入，使用`v-on`添加一个事件监听器，示例：
```
 /*-------------用户输入---"v-on"--------------------------*/
  //html
    <div id="app-5">
      <p>{{ message }}</p>
      <button v-on:click="reverseMessage">逆转消息</button>
    </div>
  //JS文件
  var app5 = new Vue({
    el: '#app-5',
    data: {
      message: 'Hello Vue.js!'
    },
    methods: {
      reverseMessage: function () {
        this.message = this.message.split('').reverse().join('')
      }
    }
  })

```
+ `v-model`,实现表单输入和应用状态之间的双向绑定，示例：
```
 /*-------------用户输入---"v-on"--------------------------*/
  //html
    <div id="app-6">
      <p>{{ message }}</p>
      <input v-model="message">
    </div>
  //JS文件
  var app6 = new Vue({
      el: '#app-6',
      data: {
        message: 'Hello Vue!'
      }
    })
```
+ 组件化应用构建，一个组件本质上是一个拥有预定义选项的一个vue实例；示例代码;
```
//html
    <div id="app-7">
      <ol>
        <!--
          现在我们为每个 todo-item 提供 todo 对象
          todo 对象是变量，即其内容可以是动态的。
          我们也需要为每个组件提供一个“key”，稍后再
          作详细解释。
        -->
        <todo-item
          v-for="item in groceryList"
          v-bind:todo="item"
          v-bind:key="item.id">
        </todo-item>
      </ol>
    </div>
//js
    Vue.component('todo-item', {
      props: ['todo'],
      template: '<li>{{ todo.text }}</li>'
    })

    var app7 = new Vue({
      el: '#app-7',
      data: {
        groceryList: [
          { id: 0, text: '蔬菜' },
          { id: 1, text: '奶酪' },
          { id: 2, text: '随便其它什么人吃的东西' }
        ]
      }
    })
```
+ Vue有点：(1) Vue 组件不需要任何polyfill，并且在所有支持的浏览器(IE9及更高版本)之下表现一致；(2)Vue 最突出的功能：跨组件数据流、自定义事件通信及构建工具集成


## 四、数据与方法

> 使用`Object.freeze()`，会阻止修改现有的属性，意味着响应系统无法再追踪变化

## 五、实例生命周期钩子

> Vue实例的初始化过程：设置数据监听、编译模板、将实例挂载到DOM并再数据变化时更新DOM等。

+ `created` 用来在一个实例被创建之后执行代码：
```
  new Vue({
    data: {
      a: 1
    },
    created: function () {
      // `this` 指向 vm 实例
      console.log('a is: ' + this.a)
    }
  })
  // => "a is: 1"
```
+ `mounted` ，`updated`, `destroyed`；生命周期钩子的`this`上下文指向调用它的Vue实例

**注：**: 不要在选项属性或回调上使用**箭头函数**，因为箭头函数是和父级上下文绑定在一起的。


## 六、模板语法

+ 文本，最常见的是使用“Mustache”语法(双大括号)的文本插值
```
//Mustache 标签将会被替代为对应数据对象上 msg 属性的值,绑定对象属性改变时，插值处的内容都会更新

  <span>Message: {{ msg }}</span>
//使用" v-once "指令，可执行一次性地插值，当数据改变时，插值处的内容不会更新

  <span v-once>这个将不会改变: {{ msg }}</span>
  
  
```
+ 原始HTML，使用`v-html` ,**注：**不能使用`v-html`来复合局部模板，示例：
```
//输出真正的HTML
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
```
+ 特性,双大括号语法不能作用在HTML特性上，应该使用`v-bind`指令；布尔特性的情况下，`v-bind`工作起来略有不同，如果值为`null`、`undefined `、`false`;则则该值的特性不会被包含在渲染出来的<button>元素中；
 
```
   <div v-bind:id="dynamicId"></div>
```

+ 使用JS表达式，**限制：**每个绑定都只能包含单个表达式
```
   {{ number + 1 }}

   {{ ok ? 'YES' : 'NO' }}

   {{ message.split('').reverse().join('') }}

   <div v-bind:id="'list-' + id"></div>
```
+ 参数，一些指令能够接收一个“参数”，在指令名称之后以冒号表示;示例:
```
   <a v-bind:href="url">...</a>
```
+  修饰符，修饰符是以半角句号`.`指明的特殊后缀，用于指出一个指令应该以特殊方式绑定，例`.prevent`修饰符告诉`v-on`指令对于触发的事件调用`event.preventDefault()`;示例:
```
   <form v-on:submit.prevent="onSubmit">...</form>
```
+ 缩写， 示例：
```
// v-bind 缩写
    <!-- 完整语法 -->
    <a v-bind:href="url">...</a>

    <!-- 缩写 -->
    <a :href="url">...</a>
    
//v-on 缩写
<!-- 完整语法 -->
   <a v-on:click="doSomething">...</a>

   <!-- 缩写 -->
   <a @click="doSomething">...</a>
```









