 React

因本人是初学React，所以用了Facebook开发、创建的Create React APP,它简化了搭建React应用框架时的初始化配置过程，
一般来说，搭建React应用框架需要有Babel等转译器来实现转译，如通过WebPack构建工具运行Babel。使用Create React 
APP则可以节省这一步骤。

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
执行完成后，你会看到安装了react,react-dom，react-script，其中，react-script安装了Babel，使我们可以使用最新的
JavaScript语法，如JSX(js扩展，可以在js语句中直接使用HTML标签)，它安装了webpack以使我们进行生成和构建以及
webpack dev server ,它给了我们目前为止看到的自动重新加载行为。create-react-app是快速入门最新技术的一个好的方法。
你无需花费很多时间去学习它们，便可开始构建第一个React应用了。

补:JSX中的元素每一个都是通过一个叫做createElement的函数创建而来的,而JSX只是能帮助我们更简洁地表达创建过程的语法。

删除默认文件，Create React App将生成大量默认文件和起始代码，可根据需要进行删减;

**Create React App主要功能介绍**

create-react-app会自动提供我们之前看到的自动重新加载行为，如我们修改JSX中的值，那么浏览器会自动刷新并显示这些更改，
若在js文件中看不到对ReactDOM的引用或者此应用是如何进入页面的。请查看index.js,index.js 从应用文件导入应用，并将应
用渲染到已存在于文档中的根元素。

create-react-app是一个剋帮助构建React应用的命令行工具，借助该工具，就无需配置Webpack等模块打包工具，
或者Babel等转译器。它们使用create-react-app进行预配置(并隐藏起来)，使你能够立即构建应用。[create-react-app的更新](https://reactjs.org/blog/2017/05/18/whats-new-in-create-react-app.html)

组件是React的基础材料,React的绝大多数API都是关于组件的，所以说他们确实非常重要，组件是React给我们的主要封装单元.

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

    记录下，git命令行如何设置clone的位置：在克隆之前，先用cd打开需要存放项目的文件夹，然后在git clone即可.
    然后用npm install安装该模块，需要用命令行打开该模块，然后在该模块内的文件夹里写：npm install然后还是在
    该文件夹内用node server.js来打开后台服务器.

    fetch User函数：此函数的唯一目标是获取特定的用户，问题是我们需要告诉该函数要获取哪个用户，我们可在函数
    定义时添加一个参数，并在调用函数时传入用户名称，例：
 ```
    function fetchUser(username){
    }
    fetchUser('Tyler')
 ```

    <User />这是一个非常基本的React组件，其目的是向UI(用户界面)显示一个用户，我们需要通过一种方式向User
    组件传递一个用户名，让它知道向视图显示哪个用户，为此我们可以向组件添加一个自定义属性并给它一个值，例：
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
    在写上句语句时，前台客户端提示：XML5633: 结束标记名称与对应的开始标记名称不匹配。看到这个信息，我不知道
    是哪里出了问题，因为和教学视频上写的是一样的代码；然后冷静下来寻找解决问题点：
        首先，再次核对自己编写的代码，确认没有问题，然后找谷歌、度娘，发现还是没有定位到问题。再次看下问题提
     示，说明我的标签出了问题，然后，把这句语句重写一遍，发现问题还在；接下来，把语句一点一点的写，直到出现问
     题了停下来，结果定位在className里，打开contact-remove，没有发现问题，把css语句重新写一遍，还是有问题；
     把该模块换个位置，问题还在，然后把语句全注释掉，一条一条显示，然后发现是背景图片的引用了出了问题；打开背
     景图的.svg，发现path标签结尾没有“/”，添加上后，发现错误提示没有了。
     
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
    
      Stateless Functional Components,基本上它能让你做到的是，如果你的所有类或所有组件只拥有
      render方法，那么你就不必以类的形式创建组件，而是作为一个普通的函数就可以了。现在我们不再
      调用render方法，而是返回JSX就像我们习惯的那样，现在的问题是，在我们根据this关键字的特定
      实例访问props之前，我们不访问this.props.contacts,而是从props获得它，而props实际上将是
      react传递给我们特定无状态函数式组件的第一个参数。   

无状态函数组件的特点：

    (1) 它们非常直观，你只需使用熟悉的函数就可以了。此函数会接受props作为参数，然后返回一些UI
    (2) 它不存在this关键字，你不需要担心这个函数会被什么环境所调用

    若你的所有组件，都只有render方法，你可以将它重构为一个所谓的无状态函数组件或只是一个接受
    props作为第一参数的普通函数。
    
 无状态函数组件总结：
 
    若组件不用跟踪内部状态(即它只有render()方法)，你可以将该组件声明为无状态函数式组件，最终，
    React组件只是返回要渲染的HTML的JS函数
    
状态：
 
    props指的是父组件的属性。最终，属性代表的是不可变的“只读”数据
    
    而组件的状态代表的是可变的数据，并最终会影响到页面上的渲染内容。状态在内部由组件本身管理，
    会随着时间的推移而改变，经常因为用户输入而改变
    
 如何将状态管理的复杂过程封装到单个组件中
 
    基于React的组件模型，我们能够将复杂的状态管理封装到单个组件，这使我们可以通过构建一堆小应用
    来构建一个大应用，而小应用实际上就是组件，要向我们的组件添加状态，我们需要做的是向我们的类
    添加一个状态属性，其值是一个对象，此对象表示组件的状态。每个键和对象表示该组件的一部分特定状
    态。
    
    state放在constructor()外面，意味着它是类字段，这是对语言做出新更改的提议。暂时不受JS的支持。
    但是Babel的强大转译功能支持下，我们可以使用它.Facebook的初始化状态设置
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

    一个很好的经验法则是：如果你要使用任何状态来渲染用户界面，将状态传入ListContacts组件来渲染
    此用户界面，该状态将存在于组件中的任何位置。
    
初始状态的属性：

    在定义组件的初始状态时，请避免使用props初始化该状态。这样容易引起错误，因为仅在组件首次被创
    建时，状态将使用props进行初始化。
    如下是错误的：
```
      this.state={
          user:props.user    //该方法是错误的
      }
```
    如果props被更新了，当前状态不会更新，除非组件“被刷新”。使用props生成组件的初始状态还会出现重复
    的数据，背离了可信赖的"单一数据源"的原则。

    React中的state，以下描述是正确的：
        (1) 组件的状态可以在初始化时加以定义；
        (2) 组件可以更改它自己的内部状态；
        (3) 状态应该(并且将会)在组件的整个生命周期内被更新.
        
状态总结

    通过让组件管理自己的状态，任何时候该状态发生变化了，React将知道并自动对页面做出必要的更新。
    
使用React构建UI组件的关键优势：

    (1) 如果要重新渲染页面，我们只需考虑更新状态。每次有更新时，我们不需要知道到底是页面的哪个
        部分变化了，我们不需要判断如何有效地重新渲染页面。React会对比之前的输出和新的输出，判
        断哪些改变了，并为我们做出决策。这种判断之前的输出和新的输出之间哪些变化了的流程，称之
        为“一致性比较”。
        
 如何更新React的state
 
    React向我们提供了一个辅助方法，叫做setState，例：this.setState()。
    
    使用setState的方式有两个，
      (1) 第一种是向setState传递一个函数，并将之前的状态作为第一个参数传递给该函数。此函数返
          回的对象将与当前状态合并，形成组件的新状态；例：
```
            this.setState((prevState)=>({
                count:prevState.count+1
            }))
```
      (2) 第二种方法，传入一个对象，此对象将与当前状态合并，形成组件的新状态。
       
      如果组件的新状态取决于之前的状态，则使用setState的函数方法；而在其他情况下，则使用对象
      方法。无论使用setState的方法是什么，最终结果都是一样的。
      
      无论何时调用setState,默认情况下，React都会重新渲染整个应用并更新UI，这就是为什么我们说
      在React中，用户界面只需通过一个传入状态的函数产生，一旦状态发生改变，用户界面就会自动更
      新。
      
 如何设置状态
 
    状态表示的是可改变的信息，最终会影响到所渲染的输出内容，因此组件可能还会使用this.setState()
    在其生命周期内更新其状态。每次本地状态变化时，React将通过调用其render()方法触发重新渲染组件。
    
    可以使用两种方法来使用setState().第一种是合并状态更新，即传入对象；、
    另一种是传入函数，此时，传入的函数具有单个prevState参数。当组件的新状态取决于上一个状态时，
    就需要使用函数setState()
    
    UI只是状态函数，在重置状态时，能够利用React的自动渲染功能使应用的用户真正获得动态体验。
    
setState()总结

    虽然组件在初始化时可以设置其状态，但是我们预期状态会随着时间的推移而变化(通常因为用户的输入)。
    组件能够使用this.setState()更改其内部状态。每次状态发生变化，React都会知道并调用render()来
    重新渲染该组件，这样可以快速有效的更新应用的UI。
    
组件属性类型的检查---PropTypes
 
    使用PropTypes检查组件的属性类型
        当我们向应用中实现更多的功能时，我们可能很快就发现经常需要调试我们的组件。例：
        如果传递给组件的props不是期望的数据类型(例：是对象不是数组)，怎么办呢，PropTypes是一个
        软件包，使我们能够在一开始就定义想要看到的数据类型，并在开发过程中，如果传递给组件是属性
        不是我们预期的类型，PropTypes将提醒我们。
        
        在应用中使用PropTypes，我们需要安装prop-types，语句如下：
```
      npm install  --save prop-types
```
propTypes优点：

    (1) PropTypes可以让我们指定具体的类型，给我们传递给特定组件的props，并允许我们指定它是否是
        必须的。
    (2) PropTypes能够在控制台获得警告
    
    PropTypes是在React应用中验证数据类型的很好方式，如“PropTypes.array.isRequired”,通过
    PropTypes检查数据类型有助于我们在开发阶段发现bug，确保用户获得顺畅的体验
    
受控组件(Controlled Components):

    通常，当你在Web应用中使用表单时，
    
    
      
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    








