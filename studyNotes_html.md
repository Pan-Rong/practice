
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
                Microsoft公司浏览器内核，IE6、IE7、IE8（Trident 4.0）、IE9（Trident 5.0）、IE10（Trident 6.0）及许多品牌
                浏览器的内核。其中部分浏览器的新版本是“双核”甚至是“多核”，其中一个内核是Trident，然后再增加一个其他内核。
          Gecko：
                Firefox内核，Netscape6开始采用的内核，后来的Mozilla FireFox(火狐浏览器) ，Mozilla Firefox、Mozilla SeaMonkey、
                waterfox（Firefox的64位开源版）、Iceweasel、Epiphany（早期版本）、Flock（早期版本）、K-Meleon使用的内核。
          Presto：
                Opera前内核，已废弃，Opera现已改用Google Chrome的Blink内核。
          Webkit：
                Safari内核,Chrome内核原型,开源，它是苹果公司自己的内核，也是苹果的Safari浏览器使用的内核。傲游浏览器3、Apple 
                Safari、(Win/Mac/iPhone/iPad)、Symbian手机浏览器、Android 默认浏览器。
          Blink：
                Blink是一个由Google和Opera Software开发的浏览器排版引擎，Google计划将这个渲染引擎作为Chromium计划的一部分，
                这一渲染引擎是开源引擎WebKit中WebCore组件的一个分支，并且在Chrome（28及往后版本）、Opera（15及往后版本）
          edge:
                微软专门为新IE打造的引擎，速度快，目前已经基于此引擎开发了浏览器，目前IE11使用该内核，估计以后微软的新浏览器会
                继续采用该内核. 
               
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
                    这里有两层意思，第一可以使用javascript操作样式与标签，强制浏览器兼容，比如先使用javascript判断浏览器类型，
                    再操作样式与标签。可以使用User-Agent、或特定对象.
                    第二指javascript存在兼容问题,可使用jQuery、Zepto、Prototype等第三方javascript库.
## 3、前端性能优化
[英文参考1](https://developer.yahoo.com/performance/rules.html),[中文参考](http://www.cnblogs.com/developersupport/p/webpage-performance-best-practices.html)

    提高前端性能可以从以下几个方面入手：
    (1) 尽量减少HTTP请求数量，如：
            图片地图、CSS Sprite、Data URI Scheme(内联资源)、样式表合并、使用Web Font字体图标
    (2) 缓存，如http头部缓存
            <meta http-equiv="Expires" content="Tue, 01 Dec 2015 13:30:26 GMT" />
            Expires是Web服务器响应消息头字段,在响应http请求时告诉浏览器，若未过期，则直接调缓存.但请求会发生，状态为304，浏览
            器默认缓存。
    (3) 使用内容发布网络(CDN使用)//暂时没了解
    (4)DNS Prefetch //暂时没了解
    (5)将CSS样式表放在顶部
    (6)将javascript脚本放在底部
    (7)使用外部javascript和CSS
    (8)避免重定向


## HTML总体介绍

**1、BOM**

    BOM(Browser Object Model)的缩写，即浏览器对象模型，当一个浏览器页面初始化时，会在内存创建一个全局的对象，用以描述当前窗口
    的属性和状态，这个全局的对象被称为浏览器对象模型，即BOM。BOM的核心对象是window,window对象也是BOM的顶级对象，其中包含了浏览器
    6个核心模块(有人说是5个,不包括frames-HTML子框架)
        (1) Document(文档对象)
        (2) frames-HTML子框架
        (3) history
        (4) location
        (5) navigator
        (6) screen
****(1) Document(文档对象)****        
    
    渲染引擎在解析HTML代码时，会为每一个元素生成对应的DOM对象，由于元素之间有层级关系，因此整个HTML代码解析完以后，会生成一个由
    不同节点组成的树形结构，俗称DOM树，document用于描述DOM树的状态和属性，并提供了很多操作DOM的API
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
