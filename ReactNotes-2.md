## React



## 零、安装

以下是基于Facebook开发、创建的Create React APP创建的React,它简化了搭建React应用框架时的初始化配置过程，一般来说， 搭建React应用框架需要有Babel等转译器来实现转译，如通过WebPack构建工具运行Babel。使用Create React APP则可以节省这一步骤。

**搭建React运行环境**

首先，打开npm,

```

    npm install -g create-react-app

```

查看安装包的方法,找到安装包的位置(以便打开安装react)：

```

    npm list -g

```    

在命令窗口，打开create-react-app安装的文件夹，在这里输入以下命令安装react项目包(例：文件夹名称:contacts)：

```

    create-react-app contacts

```    

执行完成后，你会看到安装了react,react-dom，react-script，其中，react-script安装了Babel，使我们可以使用最新的JavaScript语

法，如JSX(js扩展，可以在js语句中直接使用HTML标签)，它安装了webpack以使我们进行生成和构建以及webpack dev server ,它给了我

们目前为止看到的自动重新加载行为。create-react-app是快速入门最新技术的一个好的方法。你无需花费很多时间去学习它们，便可开始

构建第一个React应用了。



## 一、HTML模板

使用React的网页源码，结构大致如下：

```

<!DOCTYPE html>

  <head>

    <script src="../build/react.js"></script>

    <script src="../build/react-dom.js"></script>

    <script src="../build/browser.min.js"></script>

  </head>

  <body>

    <div id="example"></div>

    <script type="text/babel">

        //** code...

    </script>

  </body>

```

***两个地方需要注意***



(1) 最后一个`<script>`的`type`属性为`text/babel`;原因是jsx语法与JS不兼容

(2) head里添加了是三个库，必须首先加载；react.js是React的核心库;react-dom.js是提供与DOM相关功能;Browser.js的作用是将JSX语法转为JS语法



## 二、ReactDOM.render()

ReactDOM.render()是React的最基本方法，用于将模板转为HTML语言，并插入指定的DOM节点。

例：

```

ReactDOM.render(

    <h1>Hello,world!</h1>

    document.getElementById('example')

);

```

## 三、JSX语法

JSX语法：HTML语言直接写在JS语言之中，不加任何引号；

JSX的基本语法规则：遇到HTML标签(以<开头)，就用HTML规则解析;遇到代码块(以{开头)，就用JS规则解析;若插入的JS变量是数组，则会展开这个数组的所有成员。



## 四、组件

React允许将代码封装成组件(component)，然后像插入普通HTML标签那样，在网页中插入这个组件。

React.createClass方法就是用于生成一个组建类。

例：

```

    var HelloMessage = React.ceateClass({

        render:function(){

            return <h1>Hello {this.props.name}</h1>

        }

    });

    ReactDOM.render(

        <HelloMessage  name="John"/>

        document.getElementById('example')

    );

```

***注***



(1) 所有的组件类都必须有自己的render()方法，用于输出组件

(2) 组件类的第一个字母必须大写，否则会报错

(3) 组件类中只能包含一个顶层标签，否则会报错

(4) 添加组件属性时，要注意，class属性需要写成className,for属性需要写成htmlFor;因为class和for是JS的保留字.



## 五、this.props.children

this.props对象的属性与组件的属性一一对应，但有一个例外：

this.props.children属性，它代表组件的所有子节点；

例：

```

var NotesList = React.createClass({

    render:function(){

        return(

            <ol>

            {

                React.Children.map(this.props.children,function(child){

                    return <li>{child}</li>;

                })

            }

            </ol>

        );

    }

});

ReactDOM.render(

    <NotesList>

        <span>Hello</span>

        <span>World</span>

    </NotesList>

    document.body

);

```

***注***



(1) this.props.children的值有三种可能：若当前组件没有子节点，它就是undefined;若有一个子节点，数据类型是object;若有多个子节点，数据类型，就是array;

(2) React提供一个工具方法React.Children来处理this.props.children.我们可以用React.Children.map来遍历子节点，而不用担心this.props.children的数据类型。



## 六、PropTypes

组件的属性可以接受任意值，所以需要一种机制，验证别人使用组件时，提供的参数是否符合要求。

组件类的PropTypes属性，就是用来验证组件实例的属性是否符合要求

例：

```

var MyTitle = React.createClass({

    propTypes = {

        title : React.PropTypes.string.isRequired

    },

    render: function(){

        return <h1>{this.props.title}</h1>

    }

});

```

此外，getDefaultProps方法用来设置组件属性的默认值

例：

```

var MyTitle = React.createClass({

    getDefaultProps : function(){

        return {

            title : "Hello World"

        };

    },

    render : function(){

        return <h1>{this.props.title}</h1>

    } 

});

ReactDOM.render(

    <MyTitle />

    document.body

);

```

## 七、获取真实的DOM节点

组件并不是真实的DOM节点，而是存在于内存之中的一种数据结构，叫做虚拟DOM。只有当它插入文档以后，才会变成真实的DOM。根据React的设计，所有的DOM变动，都先在虚拟DOM上发生，然后再将实际发生变动的部分，反映在真实DOM上，这种算法叫做DOM diff。

若需要从组件获取真实DOM的节点，这时就要用到ref属性

例：

```

var MyComponent = React.createClass({

    handleClick : function(){

        this.refs.myTextInput.focus();

    },

    render:function(){

        return(

            <div>

                <input type="text" ref="myTextInput"/>

                <input type="button" value="Focus the text input" onClick={this.handleClick}/>

            </div>

        );

    }

});

ReactDOM.render(

    <MyComponent />

    document.getElementById('example')

);

```

***注***

DOM节点中必须有个ref属性，然后this.refs.[refName]就会返回这个真实的DOM节点。但特别注意，this.refs.[refName]获取的是真实DOM，所以必须等到虚拟DOM插入文档以后，才能使用这个属性。



React组件支持的时间：

Click、KeyDown、Copy、Scroll等



## 八、this.state

组件与用户的互动，React提供了state。将组件看成一个状态机，一开始有一个初始状态，然后用户互动，导致状态变化，从而触发重新渲染UI。



***注***

this.props和this.state都用于描述组件的特性，this.props表示那些一旦定义，就不再改变的特性，而this.state是会随着用户互动而产生变化的特性。



## 九、表单

例：

```

var Input = React.createClass({

    getInitialState:function(){

        return {value:"hello"};

    },

    handleChange:function(event){

        this.setState({value:event.target.value});

    },

    render:function(){

        var value = this.state.value;

        return (

            <div>

                <input type="text" value={value} onChange={this.handleChange} />

                <p>{value}</p>

            </div>

        )

    }

});

ReactDOM.render(<Input />,document.body);

```

上例中，读取文本框中值，通过定义一个onChange事件的回调函数，以及event.target.value读取用户输入的值。



## 十、生命周期

组件的生命周期分成三个状态：



(1) Mounting:已插入真实DOM

(2) Updating:正在被重新渲染

(3) Unmounting:已移除真实DOM



React为每个状态提供了两种处理函数，will函数，在进入状态之前调用；

did函数，在进入状态之后调用，三种状态共计五种处理函数：



componentWillMount()

componentDidMount()

componentWillUpdate()

componentDidUpdate()

componentWillUnmount()



此外，React还提供两种特殊状态的处理函数

componentWillReceiveProps(),已加载组件收到新的参数时调用

shouldComponentUpdate(),组件判断是否重新渲染时调用



***注***

React组件样式是一个对象，所以第一重大括号表示这时JS语法，第二重大括号表示样式对象。例：

style={{opacity:this.state.opacity}}



## 十一、Ajax

组件的数据来源，通常通过Ajax请求从服务器获取，可以使用componentDidMount方法设置Ajax请求，等请求成功，再用this.setState方法重新渲染UI
