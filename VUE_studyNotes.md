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


















