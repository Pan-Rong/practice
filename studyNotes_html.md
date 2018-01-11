
# HTML学习笔记
## 1、HTML和HTML5的区别
[参考1](http://blog.csdn.net/coco379/article/details/52938071),[参考2](http://www.duanliang920.com/learn/web/html5/230.html),[参考3](http://blog.csdn.net/zhouziyu2011/article/details/58588947)


    （1）DOCTYPE文档类型声明不同
        html文档声明：
```
        <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "
        http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
        <html xmlns="http://www.w3.org/1999/xhtml">
````
        HTML5只需要写<!DOCTYPE html>,且向下兼容;因为HTML5不是SGML(标准通用置标语言)的子集,而SGML文档中需要一个文档类
        型定义(DTD).
    （2）在结构语义上有区别
        html5新增加很多语义化标签，如：
        <title></title>简短、描述性、唯一（提升搜索引擎排名）
        <header></header>页眉通常包括网站标志、主导航、全站链接以及搜索框
        <nav></nav>：标记导航
        <main></main>：页面主要内容，一个页面只能使用一次。如果是web应用，则包围其主要功能
        <article></article>：表示文档、页面、应用或一个独立的容器，可嵌套
        <section></section>：具有相似主题的一组内容，比如网站的主页可以分成介绍、新闻条目、联系信息等条块
        <aside></aside>：指定附注栏，包括引述、侧栏、指向文章的一组链接、广告、友情链接、相关产品列表等
        <footer></footer>：页脚，只有当父级是body时，才是整个页面的页脚
        <small></small>：指定细则，输入免责声明、注解、署名、版权。
        <mark></mark>：突出显示文本（yellow），提醒读者
        <figure></figure>：创建图（默认有40px左右margin）
        <figcaption></figcaption>：figure的标题，必须是figure内嵌的第一个或者最后一个元素
        <cite></cite>：指明引用或者参考，如图书的标题，歌曲、电影等的名称，演唱会、音乐会、规范、报纸、或法律文件等
        <blockquoto></blockquoto>：引述文本，默认新的一行显示
        <q></q>：短的引述（跨浏览器问题，尽量避免使用）
        <time></time>：标记时间。datetime属性遵循特定格式，如果忽略此属性，文本内容必须是合法的日期或者时间格式
        <abbr></abbr>：解释缩写词。使用title属性可提供全称，只在第一次出现时使用就ok
        <dfn></dfn>：定义术语元素，与定义必须紧挨着，可以在描述列表dl元素中使用
        <address></address>：作者、相关人士或组织的联系信息（电子邮件地址、指向联系信息页的链接）
        <del></del>：移除的内容
        <ins></ins>：添加的内容
        <code></code>：标记代码。包含示例代码或者文件名
        <pre></pre>：预格式化文本。保留文本固有的换行和空格
        <meter></meter>：表示分数的值或者已知范围的测量结果。如投票结果。
        <progress></progress>：完成进度。可通过js动态更新value。
    （3）html5新增特性
        强大的绘图功能部分功能如下：
        <canvas>通过 JavaScript 来绘制 2D 图形，Canvas 是逐像素进行渲染的。
        <video>和<audio>用于媒介回放
        <localStorage>Web Storage的本地存储
        <sessionStorage>会话存储
        
## 2、浏览器兼容问题
[参考1](https://www.cnblogs.com/zhangyongl/p/6154981.html#undefined),[浏览器市场份额查询](https://www.netmarketshare.com),[浏览器兼容在线测试](http://browsershots.org/),[css reset脚本](http://cssreset.com/),
[CSS Hack查询](http://browserhacks.com/)

    (1)浏览器内核介绍：
          Trident：
                Microsoft公司浏览器内核，IE6、IE7、IE8（Trident 4.0）、IE9（Trident 5.0）、IE10（Trident 6.0）及许多
                品牌浏览器的内核。其中部分浏览器的新版本是“双核”甚至是“多核”，其中一个内核是Trident，然后再增加一个其他内核。
          Gecko：
                Firefox内核，Netscape6开始采用的内核，后来的Mozilla FireFox(火狐浏览器) ，Mozilla Firefox、Mozilla 
                SeaMonkey、waterfox（Firefox的64位开源版）、Iceweasel、Epiphany（早期版本）、Flock（早期版本）、K-Meleon
                使用的内核。
          Presto：
                Opera前内核，已废弃，Opera现已改用Google Chrome的Blink内核。
          Webkit：
                Safari内核,Chrome内核原型,开源，它是苹果公司自己的内核，也是苹果的Safari浏览器使用的内核。傲游浏览器3、
                Apple Safari、(Win/Mac/iPhone/iPad)、Symbian手机浏览器、Android 默认浏览器。
          Blink：
                Blink是一个由Google和Opera Software开发的浏览器排版引擎，Google计划将这个渲染引擎作为Chromium计划的一部
                分,这一渲染引擎是开源引擎WebKit中WebCore组件的一个分支，并且在Chrome（28及往后版本）、Opera（15及往后版本）
          edge:
                微软专门为新IE打造的引擎，速度快，目前已经基于此引擎开发了浏览器，目前IE11使用该内核，估计以后微软的新浏览器
                会继续采用该内核. 
               
    (2) CSS Reset:
          每种浏览器都有一套默认的样式表，即user agent stylesheet，网页在没有指定的样式时，按浏览器内置的样式表来渲染.
    (3) CSS Hack:
          CSS Hack就是针对不同的浏览器或不同版本浏览器写特定的CSS样式达到让浏览器兼容的过程
                条件注释法:
                    IE条件注释（Conditional comments）是IE浏览器私有的代码，在其它浏览器中被视为注释,例: 
```
<!--[if IE]>
                    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN">
                    <![endif]>-->
```
                样式内属性标记法,例:
```
                    _background-color:green;/*Only works in IE6*/
```
                选择器前缀法,例:     
                    *html *前缀只对IE6生效
                    *+html *+前缀只对IE7生效
                    @media screen\9{...}只对IE6/7生效 
                文档模式 （X-UA-Compatible），例：
                    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" >
                javascript兼容
                    这里有两层意思，第一可以使用javascript操作样式与标签，强制浏览器兼容，比如先使用javascript判断浏览
                    器类型，再操作样式与标签。可以使用User-Agent、或特定对象.
                    第二指javascript存在兼容问题,可使用jQuery、Zepto、Prototype等第三方javascript库.
## 3、前端性能优化
[英文参考1](https://developer.yahoo.com/performance/rules.html),[中文参考](http://www.cnblogs.com/developersupport/p/webpage-performance-best-practices.html)

    提高前端性能可以从以下几个方面入手：
    (1) 尽量减少HTTP请求数量，如：
            图片地图、CSS Sprite、Data URI Scheme(内联资源)、样式表合并、使用Web Font字体图标
    (2) 缓存，如http头部缓存
            <meta http-equiv="Expires" content="Tue, 01 Dec 2015 13:30:26 GMT" />
            Expires是Web服务器响应消息头字段,在响应http请求时告诉浏览器，若未过期，则直接调缓存.但请求会发生，状态为304，
            浏览器默认缓存。
    (3) 使用内容发布网络(CDN使用)//暂时没了解
    (4)DNS Prefetch //暂时没了解
    (5)将CSS样式表放在顶部
    (6)将javascript脚本放在底部
    (7)使用外部javascript和CSS
    (8)避免重定向


## HTML总体介绍

**1、BOM**

    BOM(Browser Object Model)的缩写，即浏览器对象模型，当一个浏览器页面初始化时，会在内存创建一个全局的对象，用以描述当前
    窗口的属性和状态，这个全局的对象被称为浏览器对象模型，即BOM。BOM的核心对象是window,window对象也是BOM的顶级对象，其中包
    含了浏览器6个核心模块(有人说是5个,不包括frames-HTML子框架)
        (1) Document(文档对象)
        (2) frames-HTML子框架
        (3) history
        (4) location
        (5) navigator
        (6) screen

****(1) Document(文档对象)****        
    
    渲染引擎在解析HTML代码时，会为每一个元素生成对应的DOM对象，由于元素之间有层级关系，因此整个HTML代码解析完以后，会生成
    一个由不同节点组成的树形结构，俗称DOM树，document用于描述DOM树的状态和属性，并提供了很多操作DOM的API

****(2) frames-HTML子框架****      
    
    即在浏览器里嵌入另一个窗口，父框架和子框架拥有独立的作用域和上下文
    
****(3) history****     
    
    以栈(FIFO)的形式保存着页面被访问的历史记录，页面前进即入栈，页面返回即出栈
    
****(4) location****   
    
    提供了当前窗口中加载的文档相关信息以及一些导航功能
    
****(5) navigator****     
    
    用来描述浏览器本身，包括浏览器的名称、版本、语言、系统平台，用户特性字符串等
    
****(6) screen****      
    
    提供了浏览器显示屏幕的相关属性，如：显示屏的宽度和高度，可用宽度和高度
    
**2、DOM**    
    
    DOM将HTML和XML文档映射成一个由不同节点组成的树型结构，其核心是document
    
**3、事件系统**
    
    事件是用户与页面交互的基础，到目前为止，DOM事件从PC端的鼠标事件(mouse)发展到移动端的触摸事件(touch)
    和手势事件(guesture),touch事件描述了手指在屏幕操作的每一个细节，guesture则描述多手指操作时的复杂情况
    如：
        第一根手指放下，触发touchmove
        第二根手指放下，触发gesturestart
        触发第二根手指的touchstart，立即触发gesturechange
        任意手指移动，持续触发gesturechange
        第二根手指弹起时，触发gestureend,以后将不会再触发gesturechange;触发第二根手指的touchend
        触发touchstart(多根手指在屏幕上，提起一根，会刷新一次全局touch)
        弹起第一根手指，触发touchend
        
     DOM2.0模型将事件处理流程分为三个阶段：事件捕获阶段、事件处理阶段、事件冒泡阶段
        (1)事件捕获：当用户触发点击事件后，顶层对象document就会发出一个事件流，从最外层DOM节点向目标元素节点传递，最终到达目
            标元素
        (2)事件处理：当到达目标元素之后，执行目标元素绑定的处理函数。如果没有绑定监听函数，则不做任何处理。
        (3)事件冒泡：事件流从目标元素开始，向最外层DOM节点传递，途中如果有节点绑定了事件处理函数，这些函数将会被执行；
        
        利用事件冒泡原理，可以实现事件委托，所谓委托，就是在父元素上添加监听器，用以监听和处理子元素的事件，避免重复为子元素绑
        定相同的事件，当目标元素的事件被触发以后，这个事件就从目标元素开始，向最外层元素传递，最终冒泡到父元素上，父元素在通过
        event.targe获取到这个目标元素(之前作品中用this也可以)。这样做的好处是，父元素只需绑定一个事件监听，即可以对所有子元素
        的事件进行处理，从而减少不必要的事件绑定，对页面性能有一定的提升。
        
**4、HTML解析过程**        
    
    (1)浏览器加载html文件
    (2)渲染并解析HTML标签，生成DOM节点
    (3)渲染并解析CSS样式，生成CSSOM
    (4)js脚本处理
    (5)将以上打包渲染到浏览器上
      
**5、重绘和回流**

    回流：当渲染树中的一部分(或全部)因为元素的规模尺寸、布局、隐藏(主要是display)等改变而需要重新构建；
    重绘：当渲染树中的一些元素需要更新属性，而这些属性只是影响元素的外观、风格；而不会影响布局时，就叫重绘；
    由此可知，回流必会引起重绘，而重绘不一定会引起回流
    
    注：transform操作不会引起重绘和回流，是一种高效率的渲染。因为transform属于合成属性，对合成属性进行transition
        或animation动画时将会创建一个合成层，这使得动画元素在一个独立的层中进行渲染，当元素的内容没有发生改变，就
        不会重绘和回流。
        
**6、本地存储**

    (1) cookie
        
        最原始方式，数据以键值对形式保存，可设置过期时间；但不适合大量数据存储；因为每请求一次页面，cookie都会发送给
        服务器，因此被限制在4K左右(因浏览器而异)，超出即被忽略，且永不会被设置
        
    (2) localStorage和sessionStorage
        
        这是HTML5提供的两种方式，都是以键值对的形式来存储数据；前者是永久存储，后者的存储仅限于浏览器会话(session)。
        即当浏览器窗口关闭后，sessionStorage中的数据被清除。
        
        localStorage的存储空间约5M，但在浏览器隐私模式下不可读取，数据超出时会抛异常。
        
**7、浏览器缓存机制**
        
    浏览器缓存机制是通过HTTP协议头里的Cache-Control(或Expires)和Last-Modified(或Etag)等字段来控制文件缓存的机制；
    Cache-Control用于控制文本在本地缓存有效时长。最常见的，如Cache-Control:max-age=600,表示文件在本地应该缓存，且有
    效时长为600s
    
    Last-Modified是标识文件在服务器上的最新更新时间；若到期，且没有修改，则服务器则返回304告诉浏览器继续用该缓存数据。
    
**8、History**
    
    用户访问网页的历史记录通常会被保存在一个类似于栈的对象中，即history对象，点击返回就出栈，跳下一页就入栈。
    
**9、HTML5离线缓存**

    HTML5离线缓存又叫Application Cache，是从浏览器的缓存中分出来的一块缓存区，如果要在这个缓存中保存数据，可以使用一个
    描述文件(manifest file)

**10、Web语义化和SEO**

    Web语义化是指使用语义恰当的标签，是页面有良好的结构，页面元素有含义，能够让人和搜索引擎都容易理解。
    
    SEO是指了解搜索引擎自然排名机制的基础之上，对网站进行内部及外部的调整优化，改进网站在搜索引擎中关键词的自然排名，获得
    更多的展现量，吸引更多目标客户点击访问网站，从而达到互联网营销及品牌建设的目标。
    
    搜索引擎通过爬虫技术获取的页面就是由一堆html标签组成的代码，人可以通过可视化的方式来判断页面上哪些内容是重点，而机器
    不行。但搜索引擎会根据标签的含义来判断内容的权重，因此，在合适的位置使用恰当的标签，使整个页面的语义明确，结构清晰，
    搜索引擎才能正确识别页面中重要内容，并予以较高的权值。
