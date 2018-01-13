# React[中文文档](https://doc.react-china.org/docs/hello-world.html)

## React 的优点

    提问：为什么要学React，它是什么。
    
React的优点：

    (1) 声明式(与命令式的区别：声明式只要知道目的，不需要知道具体步骤)
        因为React是声明式的JS，可以非常轻松的创建用户交互界面。为你应用的每一个状态设计简介的视图，在数据改变时React也可以
        高效地更新渲染界面.以声明式编写的UI，可以让你的代码更加可靠，且方便调试。    
    (2) 组件化
        React的组件化的特点，可以让开发者创建好拥有各自状态的组件，再由组件构成更加复杂的界面。
        无需再用模板代码，通过使用JS编写的组件就可以更好地传递数据，将应用状态和DOM拆分开来.
    (3) 方便(一次学习，随处编写)
        无论你现在正在使用什么技术栈，你都可以随时引入React开发新特性。
        React也可以用作开发原生应用的框架--React Native.

    上述提问的回答：React 是一款非常火热的JS库(就是JS)，可用于快速更新DOM，但它实际上只能处理视图，而非整个应用。 
## React简介

    (1) React组件：使用一个名为render()的方法，接收数据作为输入，输出页面中对应展示的内容。
    (2) 有状态组件: 除了使用外部传入的数据外(通过this.props访问传入数据)，组件还可以拥有其他内部的状态数据(通过
        this.state访问状态数据)。当组件的状态数据改变时，组件会调用render()方法重新渲染。
    (3) 应用   
        使用props和state,我们可以创建一个简易的Todo应用(待办事项应用)。    
    (4) 在组件中使用第三方库
        React提供了可调用其他第三方框架或库的接口。   
## React的应用(待进一步整理)

以下是基于Facebook开发、创建的Create React APP创建的React,它简化了搭建React应用框架时的初始化配置过程，一般来说，
搭建React应用框架需要有Babel等转译器来实现转译，如通过WebPack构建工具运行Babel。使用Create React APP则可以节省这一步骤。

**搭建React运行环境**

首先，打开npm,npm具体操作方法见[npm笔记](https://github.com/Pan-Rong/practice/blob/master/studyNotes_NPM.md)

安装一个全局的Create React App,NPM的命令行如下：
```
    npm install -g create-react-app
```
查看安装包的方法,找到安装包的位置(以便打开安装react)：
```
    npm list -g
```
在命令窗口，打开create-react-app安装的文件夹，在这里输入以下命令安装react项目包(文件夹名称:contacts)：
```
    create-react-app contacts
```

    执行完成后，你会看到安装了react,react-dom，react-script，其中，react-script安装了Babel，使我们可以使用最新的JavaScript语
    法，如JSX(js扩展，可以在js语句中直接使用HTML标签)，它安装了webpack以使我们进行生成和构建以及webpack dev server ,它给了我
    们目前为止看到的自动重新加载行为。create-react-app是快速入门最新技术的一个好的方法。你无需花费很多时间去学习它们，便可开始
    构建第一个React应用了。

    补:JSX中的元素每一个都是通过一个叫做createElement的函数创建而来的,而JSX只是能帮助我们更简洁地表达创建过程的语法。

    删除默认文件，Create React App将生成大量默认文件和起始代码，可根据需要进行删减;

**Create React App主要功能介绍**[create-react-app的更新](https://reactjs.org/blog/2017/05/18/whats-new-in-create-react-app.html)

    create-react-app会自动提供我们之前看到的自动重新加载行为，如我们修改JSX中的值，那么浏览器会自动刷新并显示这些更改，
    若在js文件中看不到对ReactDOM的引用或者此应用是如何进入页面的。请查看index.js,index.js 从应用文件导入应用，并将应
    用渲染到已存在于文档中的根元素。

    create-react-app是一个剋帮助构建React应用的命令行工具，借助该工具，就无需配置Webpack等模块打包工具，
    或者Babel等转译器。它们使用create-react-app进行预配置(并隐藏起来)，使你能够立即构建应用。

    组件是React的基础材料,React的绝大多数API都是关于组件的，们确实非常重要，组件是React给我们的主要封装单元.

组件的优点：

    (1) 可以帮助我们将UI分解成小块，这些小块都有明确的责任和清除定义的界面，在构建大型应用时，这真的非常非常重要，
        它可以让我们在应用的小块上工作，而不会不经意地影响其他块。
    (2) 让我们使用组合，而不是继承来构建应用程序.
    (3) 组件有一个非常好的特性：具有明确的接口，所以可以通过给它们不同的props来配置不同的组件。

目前用的比较多的组件是：Contactlist组件

**React的新概念**

    (1) props :你可以通过它将数据传入组件中;
    (2) functional Components函数式组件，它是可选的，并且是一种更加符合直觉的方式，去创建React组件;
    (3) controlled Components受控组件，它可以让你将应用中的表单，连接到组件状态.
    
**React的优点**

    (1) 你可以将使用函数的直觉应用于创建React组件中
    (2) 我们可以拥有动态的state而不是存储在APP文件中，我们可以创建一个组件来处理处理显示
    (3) 能让我们的大脑分开两个重要又复杂的概念：第一，组件看起来是什么样；第二，应用当前的状态是什么。
    
    
**React的学习过程**

按上述描述搭建React运行环境后，需要从github上下载相关代码：

    记录下，git命令行如何设置clone的位置：在克隆之前，先用cd打开需要存放项目的文件夹，然后在git clone即可.然后用npm 
    install安装该模块，需要用命令行打开该模块，然后在该模块内的文件夹里写：npm install然后还是在该文件夹内用node 
    server.js来打开后台服务器.

    fetch User函数：此函数的唯一目标是获取特定的用户，问题是我们需要告诉该函数要获取哪个用户，我们可在函数定义时添加
    一个参数，并在调用函数时传入用户名称，例：
```
    function fetchUser(username){ }
    fetchUser('Tyler')
```
    <User />这是一个非常基本的React组件，其目的是向UI(用户界面)显示一个用户，我们需要通过一种方式向User组件传递一个
    用户名，让它知道向视图显示哪个用户，为此我们可以向组件添加一个自定义属性并给它一个值，例：
    <User username='Tyler'/>

    现在我们可以使用this.props.username从组件内部访问该值，例：
```
      class User extends React.Component{
            render(){
                return(
                    <p>Username:{this.props.username}</p>
                )
            }
      }
      <User username='Tyler' />
```
事实上  ，添加到一个组件的任何属性，都可在该组件内的prop对象上访问，例：
```
    class User extends React.Component{
          render(){
              return(
                  <div>
                      <p>Username:{this.props.username}</p>
                      <p>Is Friend?:{this.props.friend}</p>
                  </div>
              )
          }
    }
    <User username='Tyler' friend={true} />
    <User username='Tyler' />
```
过程中遇到的问题及解决步骤
```
      <button className='contact-remove'>Remove</button>
```
    在写上句语句时，前台客户端提示：XML5633: 结束标记名称与对应的开始标记名称不匹配。看到这个信息，我不知道是哪里出了问
    题，因为和教学视频上写的是一样的代码；然后冷静下来寻找解决问题点：
        首先，再次核对自己编写的代码，确认没有问题，然后找谷歌、度娘，发现还是没有定位到问题。再次看下问题提示，说明我的
    标签出了问题，然后，把这句语句重写一遍，发现问题还在；接下来，把语句一点一点的写，直到出现问题了停下来，结果定位在
    className里，打开contact-remove，没有发现问题，把css语句重新写一遍，还是有问题；把该模块换个位置，问题还在，然后
    把语句全注释掉，一条一条显示，然后发现是背景图片的引用了出了问题；打开背景图的.svg，发现path标签结尾没有“/”，添加
    上后，发现错误提示没有了。

    由此可知，在React中，即使是单闭合标签，也一定要在结尾加“/”，不能向之前在HTML5里，直接省略不写.

使用props传递数据总结

    props是传递给React组件的任何输入内容。就像HTML属性一样，props名称和值会添加到组件中。
    例：
```
    //passing a prop to a component
    <LogoutButton text='Wanna log out?' />
```
    上述代码中，text是props的字符串‘Wanna log out’的值
    
    所有属性都存储在this.props对象上，因此，要在组件中访问此text props，我们使用this.props.text,
    例：
```
    //access the prop inside the component
    ...
    render(){
        return <div>{this.props.text}</div>
    }
    ...
```

对props的认识

    可以用看待参数和函数的关系，来看待props与组件的关系

无状态函数组件：

    Stateless Functional Components,基本上它能让你做到的是，如果你的所有类或所有组件只拥有render方法，那么你
    就不必以类的形式创建组件，而是作为一个普通的函数就可以了。现在我们不再调用render方法，而是返回JSX就像我们习
    惯的那样，现在的问题是，在我们根据this关键字的特定实例访问props之前，我们不访问this.props.contacts,而是从
    props获得它，而props实际上将是react传递给我们特定无状态函数式组件的第一个参数。   

无状态函数组件的特点：

    (1) 它们非常直观，你只需使用熟悉的函数就可以了。此函数会接受props作为参数，然后返回一些UI
    (2) 它不存在this关键字，你不需要担心这个函数会被什么环境所调用

    若你的所有组件，都只有render方法，你可以将它重构为一个所谓的无状态函数组件或只是一个接受props作为第一参数的普
    通函数。

无状态函数组件总结：

    若组件不用跟踪内部状态(即它只有render()方法)，你可以将该组件声明为无状态函数式组件，最终，React组件只是返回要
    渲染的HTML的JS函数

状态：

    props指的是父组件的属性。最终，属性代表的是不可变的“只读”数据

    而组件的状态代表的是可变的数据，并最终会影响到页面上的渲染内容。状态在内部由组件本身管理，会随着时间的推移而改
    变，经常因为用户输入而改变.

如何将状态管理的复杂过程封装到单个组件中

    基于React的组件模型，我们能够将复杂的状态管理封装到单个组件，这使我们可以通过构建一堆小应用来构建一个大应用，
    而小应用实际上就是组件，要向我们的组件添加状态，我们需要做的是向我们的类添加一个状态属性，其值是一个对象，此
    对象表示组件的状态。每个键和对象表示该组件的一部分特定状态。

    state放在constructor()外面，意味着它是类字段，这是对语言做出新更改的提议。暂时不受JS的支持。但是Babel的强大
    转译功能支持下，我们可以使用它.Facebook的初始化状态设置.
```
    class User extends React.Component{
          constructor(props){
              super(props);
              this.state={
                  username:'Tyler'
              }
          }
    }
```
    一个很好的经验法则是：如果你要使用任何状态来渲染用户界面，将状态传入ListContacts组件来渲染此用户界面，该状态
    将存在于组件中的任何位置。

初始状态的属性：

    在定义组件的初始状态时，请避免使用props初始化该状态。这样容易引起错误，因为仅在组件首次被创建时，状态将使用
    props进行初始化。如下是错误的：
```
      this.state={
          user:props.user    //该方法是错误的
      }
```
    如果props被更新了，当前状态不会更新，除非组件“被刷新”。使用props生成组件的初始状态还会出现重复的数据，背离了
    可信赖的"单一数据源"的原则。

    React中的state，以下描述是正确的：
        (1) 组件的状态可以在初始化时加以定义；
        (2) 组件可以更改它自己的内部状态；
        (3) 状态应该(并且将会)在组件的整个生命周期内被更新.

状态总结

    通过让组件管理自己的状态，任何时候该状态发生变化了，React将知道并自动对页面做出必要的更新。

使用React构建UI组件的关键优势：

    如果要重新渲染页面，我们只需考虑更新状态。每次有更新时，我们不需要知道到底是页面的哪个部分变化了，我
    们不需要判断如何有效地重新渲染页面。React会对比之前的输出和新的输出，判断哪些改变了，并为我们做出决
    策。这种判断之前的输出和新的输出之间哪些变化了的流程，称之为“一致性比较”。

如何更新React的state 

    React向我们提供了一个辅助方法，叫做setState，例：this.setState()。

    使用setState的方式有两个，
    (1) 第一种是向setState传递一个函数，并将之前的状态作为第一个参数传递给该函数。此函数返回的对象将
        与当前状态合并，形成组件的新状态；例：
```
            this.setState((prevState)=>({
                count:prevState.count+1
            }))
```
    (2) 第二种方法，传入一个对象，此对象将与当前状态合并，形成组件的新状态。

    如果组件的新状态取决于之前的状态，则使用setState的函数方法；而在其他情况下，则使用对象方法。无论使用
    setState的方法是什么，最终结果都是一样的。

    无论何时调用setState,默认情况下，React都会重新渲染整个应用并更新UI，这就是为什么我们说在React中，用
    户界面只需通过一个传入状态的函数产生，一旦状态发生改变，用户界面就会自动更新。

如何设置状态

    状态表示的是可改变的信息，最终会影响到所渲染的输出内容，因此组件可能还会使用this.setState()在其生命周
    期内更新其状态。每次本地状态变化时，React将通过调用其render()方法触发重新渲染组件。

    可以使用两种方法来使用setState().第一种是合并状态更新，即传入对象；另一种是传入函数，此时，传入的函数
    具有单个prevState参数。当组件的新状态取决于上一个状态时，就需要使用函数setState()

    UI只是状态函数，在重置状态时，能够利用React的自动渲染功能使应用的用户真正获得动态体验。

setState()总结

    虽然组件在初始化时可以设置其状态，但是我们预期状态会随着时间的推移而变化(通常因为用户的输入)。组件能够使
    用this.setState()更改其内部状态。每次状态发生变化，React都会知道并调用render()来重新渲染该组件，这样可
    以快速有效的更新应用的UI。

组件属性类型的检查---PropTypes

    使用PropTypes检查组件的属性类型
        当我们向应用中实现更多的功能时，我们可能很快就发现经常需要调试我们的组件。例：
        如果传递给组件的props不是期望的数据类型(例：是对象不是数组)，怎么办呢，PropTypes是一个软件包，使我们
        能够在一开始就定义想要看到的数据类型，并在开发过程中，如果传递给组件是属性不是我们预期的类型，PropTypes
        将提醒我们。

    在应用中使用PropTypes，我们需要安装prop-types，语句如下：
```
      npm install  --save prop-types
```
propTypes优点：

    (1) PropTypes可以让我们指定具体的类型，给我们传递给特定组件的props，并允许我们指定它是否是必须的。
    (2) PropTypes能够在控制台获得警告

    PropTypes是在React应用中验证数据类型的很好方式，如“PropTypes.array.isRequired”,通过PropTypes检
    查数据类型有助于我们在开发阶段发现bug，确保用户获得顺畅的体验

受控组件(Controlled Components):

    通常，当你在Web应用中使用表单时，表单状态会位于DOM内，React的主要作用在于更有效地管理你的应用程序的
    状态。所以表单状态通常存在于DOM内，但是React进行所有的状态管理，那如何处理React中的表单呢？我们通过
    React的受控组件来解决这个问题。

    受控组件是渲染表单的组件，但表单状态的来源，位于组件状态内，而非DOM内，它们被称为受控组件的原因是因为
    React在控制表单的状态。

    受控组件的代码会稍多点，但是优势很明显：
    (1) 它们支持即时输入验证
    (2) 它们允许你有条件地禁用或启用表单按钮
    (3) 它们限制了输入的格式
    以上优点都涉及根据用户输入更新，这不仅是受控组件，也是React的核心特征：如果应用的状态发生变化。那么我们
    的UI会根据新状态进行更新。

React开发工具

    作用：使你能够检查组件的层次结构以及各自的属性和状态

受控组件总结

    受控组件是指渲染表格的组件，但是该表格状态的数据源位于组件状态里，而不是DOM里，受控组件的优势：
    (1) 立即验证输入
    (2) 有条件地停用/启用按钮
    (3) 控制输入格式

React中状态管理的总结：

    在跟踪应用数据时，思考下需要如何处理该数据，并当用户查看应用界面时，数据的外观看起来如何。如果你希望组件
    存储可变的本地数据，可以考虑使用状态存储该信息。很多时候，系统会使用状态管理组件中的受控表格元素。

    另一方面，如果某些信息一直不会变化，在整个应用中基本上是"只读"状态，可以考虑改为使用属性，状态和属性通常
    都是对象形式。更改任何一个都会触发重新渲染组件，但是它们各自在应用中扮演了截然不同的角色。
 
 外部数据渲染UI

    如何存储和管理处在于某个数据库中的数据。
    render方法不能有副作用，它不能发出Ajax请求或执行具有异步性质的任何操作。它只能接收props并返回对此UI的描述。
    那React是在哪里发出Ajax请求的呢？这就引进了React中的lifecycle events(生命周期事件)的概念。
    lifecycle event是每个组件具有的特殊方法，允许我们在组件生命的某些事件运行自定义行为。比如，当组件被创建和
    插入DOM中时，当组件接收props时等等。

    React拥有大量不同生命周期事件，可供使用。以下是常用的几种：
    首先：componentWillMount,它在组件插入DOM之前立即调用
    接下来：componentDidMount,它在组件插入DOM之后立即调用
    然后：componentWillUnmount,它在组件从DOM移除之前立即调用
    最后：componentWillRecieveProps,它在组件即将接收全新的props时调用

    如果我们想从API获取外部数据，要怎么做？
    这正是使用componentDidMount生命周期事件的最佳时机。

    render方法仅用于渲染，不应在render方法中获取数据。组件render方法应该仅用于渲染组件；不应该发出任何HTTP请求，
    获取用于显示内容的数据，或者更高DOM。此外，render方法不应该调用任何执行这些操作的其他函数。

    因为React中render方法仅用于显示内容，我们将应该处理Ajax请求等任务的代码放在React的生命周期事件中。

What is 生命周期？

    生命周期事件是组件中名称特殊的方法。这些方法会自动绑定到组件实例。React将在组件生命周期的特定时间点调用这些方
    法。要使用其中一个事件，你只需要在组件中使用相关名称创建一个方法。React将调用该方法。这样可以轻松地挂接到React
    组件的不同生命周期阶段。最最常用的是componentDidMount()生命周期事件；即在组件插入DOM之后立即被调用。

    想使用React发送Ajax请求，需要使用componentDidMount这个生命周期事件，让我们来看看它的工作原理：
        在我们的组件添加到视图后，componentDidMount将被掉调用并发起Ajax请求，一旦请求完成并返回正确的相应后
        setState将被调用，这会使用最新请求的数据更新我们的组件状态。这将会重新渲染组件并更新UI，例：
```
      componentDidMount(){
         fetchUser().then(user=>this.setState({
              name:user.name
              age:user.age
         }))
      } 
```
    componentDidMount()在组件装载后立即被调用，应该在需要初始化DOM节点的时候使用该方法。如果你想从远程端点加载数
    据，那么此处适合实现网络请求。在此方法中设置状态将触发重新渲染。例：
```
     import React,{Component} from 'react';
     import fetchUser from '../utils/UserAPI';
     
     class User extends Component{
         constructor(props){
            super(props)
            this.state={
                 name:''
                 age:''
            }
         }
         componentDidMount(){
            fetchUser().then(user)=>this.setState({
                 name:user.name
                 age:user.age
            })
         }
         render(){
            return(
                <div>
                     <p>Name:{this.state.name}</p>
                     <p>Age:{this.state.age}</p>
                </div>
            )
         }
     }
     export default User;
```
    上例中的componentDidMount()生命周期事件的工作原理：
    (1) render()方法被调用，然后它会更新具有<div>的页面(一段是名字，一段是年龄)。值得注意的是，this.state.name
        和this.state.age是空字符串(一开始)，所以名称和年龄实际上并不显示出来。
    (2) 组件被装载后，发出componentDidMount()生命周期事件
        (1) 运行UserAPI的fetchUser请求，它会向用户数据库发出请求
        (2) 返回数据后，setState()被调用，并更新name和age属性
    (3) 因为状态已变化，render()再次被调用，这样就会重新渲染页面，但是现在this.state.name和this.state.age具有
        值了。

componentDidMount()总结：

    componentDidMount()是React提供的多个生命周期事件之一。当组件被“装载”后(即被渲染之后)，componentDidMount()
    被调用。如果你想动态地获取数据或运行Ajax请求，则应该在componentDidMount()中执行这些操作.s

使用外部数据渲染UI总结：

    生命周期是React提供的特殊方法，使我们能够挂接到组件生命周期的不同阶段以运行一些代码。有各种不同的生命周期事件，
    它们将在不同的时间点运行，但是我们可以将它们划分为三大类别：

    (1) 添加到DOM中，当组件正在添加到DOM中时，这些生命周期事件被调用
        constructor()
        componentWillMount()
        render()
        componentDidMount()

    (2) 重新渲染-rendering
        当组件正在重新渲染到DOM时，这些生命周期事件被调用：
        componentWillReceiveProps()
        shouldComponentUpdate()
        componentWillUpdate()
        render()
        componentDidUpdate()

    (3) 从DOM中删除
        当组件正在从DOM中被删除时，以下生命周期事件被调用：
           componentWillUnmount()

使用React Router管理应用位置信息   

    当我们在浏览器中使用JS渲染UI时，人们有时称此为“单页面应用”，这是什么意思呢？典型的网站是这样的，当用户访问网
    站时，浏览器会从网站的服务器请求页面，服务器生成一些HTML并将其返回，当用户使用导航时，浏览器会从服务器请求一
    个新页面。服务器将返回一个新页面的HTML文件给浏览器，用户便会看到新页面。以此往复；

单页面应用

    当人们说单页面应用时，并不是说应用只有一个页面，而是说浏览器不需要向服务器请求新页面，而由JS处理页面之间的转
    换。所以服务器只发送一个初始页面，这就是为什么它叫做单页面应用。React Router是让我们使用React构建单页面应
    用的一个工具。

    单页面应用可以有多种工作方式，单页面应用的一种加载方式是一次性下载整个网站的内容。这样，当你浏览网站时，一切
    内容已经出现在浏览器中，不需要刷新页面。单页面应用的另一种工作方式是下载渲染用户请求的页面所需的所有内容。当
    用户浏览到新页面时，仅对请求的内容发出异步JS请求。

    优质单页面应用的另一个关键因素是由URL控制页面内容。单页面应用互动性非常高，用户希望能够仅使用URL就能回到特
    定的状态。为何这一点很重要呢？bookmarkability(书签功能，很确定的是，这还不是一个单词)。当你将网站添加到书
    签中，该书签仅仅是URL，并没有记录该页面的状态。

    你对应用执行的任何操作都不会更新页面的URL。我们需要创建能够将页面添加到书签中的React应用

React Router

    React Router会将React项目转变成单页面应用。它通过提供大量特殊的组件来实现这一点。这些组件能够管理链接的创
    建、管理应用的URL、在不同的URL地点之间导航时提供转换。

    React Router是一系列导航式组件的集合，可以于应用一起以声明的方式编写代码。

    React Router能使用户界面和URL保持同步，它能满足用户对页面链接以及URL的所有期待.

    React Router提供了两个不同的使用场景“react-router-native”和“react-router-dom”

动态的渲染页面

    我们需要将新的UI创建为单独的组件，并使用组合功能将器包含在另一个组件里。

    短路求值语法：例：
```
    {this.state.sreen==='list'&&(
         <ListContacts />
    )}
```
    上述代码看起来可能优点迷惑，既有组件JSX代码，又有运行表达式的代码。但其实就是逻辑表达式&&：
         expression && expression

    这里使用的是一种叫做短路求值的JS技巧。如果第一个表达式的值是true，则运行第二个表达式。若第一个表达式
    是false，则跳过第二个表达式。我们使用这种技巧来首先验证this.state.screen的值，然后显示正确的组件.

BrowserRouter组件  

    BrowserRouter是React Router组件

    在使用React Router之前，我们需要通过NPM安装它。安装好后，就可以将其组件导入我们的应用中。
```
   npm install --save react-router-dom
```
    有上述React Router简介中可知， React Router提供了两个不同的使用场景“react-router-native”和
    “react-router-dom”，其中BrowserRouter使用react-router-dom场景。

    当你使用BrowserRouter时，其实真正的是在渲染Router组件并将向其传递history属性。什么是history？
    history来自history库(也是由React Training构建的)。该库的整个目标是抽象化不同环境中的区别，并提供最少
    的API来使你管理历史记录堆、导航、确认导航，并在会话之间保持状态。

    简言之：当你使用BrowserRouter时，你是在创建history对象，该对象将监听URL中的变化，并使你的应用知道这
           些变化。

BrowserRouter组件总结

    要使React Router正常工作，你需要将整个应用封装在BrowserRouter组件中，此外，BrowserRouter还会封装
    history库，使你的应用能够知道URL中的变化.

Link 组件

    Link组件是ReactRouter中的一个组件。react-router的Link组件非常重要。它使你的用户能够在应用中进行导航，
    当用户点击Link组件时，它会通知BrowserRouter使它更新URL，它还具备很好的可访问性，如果你使用键盘在应用中
    导航，它仍然可以正常工作，并右键打开新窗口的功能也依然有用。

    Link是提供声明式、可访问的应用导航的简单方式。这里补充下声明式(即只关心结果，不关心过程，嘻嘻~)。通过向
    Link组件传递to属性，可以告诉应用要路由到哪个部分。
```
    <Link to='/about'>About</Link>
```
    若你对网络上的路由熟悉，那么你将知道链接有时候需要稍微复杂下，而不仅仅只是个字符串。例如，可以传递查询参
    数或链接到页面的特定部分。如果要将状态传递给新的路由，该怎么办呢？要考虑这些情形，你可以向Link的to属性传
    递对象，而不是字符串.例：
```
    <Link to={{
         pathname:'/courses',
         search:'?sort=name',
         hash:'#the-hash',
         state:{fromDashboard:true}
    }}>
    Courses
    </Link>
```

Link总结

    React Router提供了一个Link组件，使你能够添加声明式、可访问的应用导航功能。你将在锚点标记(a标签)中使用它，
    就像通常使用的那样。React Router的<Link>组件是让用户能够导航应用的很好方式。例如，向链接传递to属性可以
    将用户指向绝对路径，例：
```
   <Link to="/about">About</Link>
```
    因为<Link>组件会渲染成拥有相应的href的锚点标签，因为，它的行为和网络上的普通链接的行为一样。

Router组件

    Route接受一个路径，将会匹配(也可能不匹配)当前的URL，如果路径匹配URL，则Route会渲染一些UI,不匹配则不会渲
    染。就像我们编写的代码，通过检查组件的状态，来决定要渲染哪个页面，Route也为我们做同样的事。只是它检查的不
    是组件的状态，而是URL，这意味着现在回退按钮可以正常工作了。

    最后让React Router为我们管理URL和UI

Router组件总结：

    若你希望向router将渲染的特定组件传递属性，你需要使用Router的render属性，render使你能够控制渲染组件，进而
    使你能够向要渲染的组件传递任何属性。
 

未完待续...
