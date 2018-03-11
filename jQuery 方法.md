# jQuery的方法汇总

**jQuery语法实例**
基础语法是：$(selector).action()

  美元符号定义 jQuery
  选择符（selector）“查询”和“查找” HTML 元素
  jQuery 的 action() 执行对元素的操作
  
例： $(this).hide() 隐藏当前的 HTML 元素;

**文档就绪函数**
$(document).ready(function(){});
这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码。

**jQuey选择器**
(1) jQuery 元素选择器
    jQuery 使用 CSS 选择器来选取 HTML 元素;
(2) jQuery 属性选择器
    jQuery 使用 XPath 表达式来选择带有给定属性的元素
例：

$("[href]") 选取所有带有 href 属性的元素。
$("[href='#']") 选取所有带有 href 值等于 "#" 的元素。
$("[href!='#']") 选取所有带有 href 值不等于 "#" 的元素。
$("[href$='.jpg']") 选取所有 href 值以 ".jpg" 结尾的元素

(3) jQuery CSS 选择器
例：
```
$("p").css("background-color","red");
```

**jQuery事件**
事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。术语由事件“触发”（或“激发”）经常会被使用。

**jQuery 名称冲突**
var jq=jQuery.noConflict()，解决名称冲突问题

jQuery处理HTML事件的原则：

(1) 把所有 jQuery 代码置于事件处理函数中
(2) 把所有事件处理函数置于文档就绪事件处理器中
(3) 把 jQuery 代码置于单独的 .js 文件中
(4) 如果存在名称冲突，则重命名 jQuery 库

**Jquery事件的举例**
(1) $(document).ready(function) 将函数绑定到文档的就绪事件（当文档完成加载时）
(2) $(selector).click(function) 触发或将函数绑定到被选元素的点击事件
(3) $(selector).dblclick(function) 触发或将函数绑定到被选元素的双击事件
(4) $(selector).focus(function) 触发或将函数绑定到被选元素的获得焦点事件
(5) $(selector).mouseover(function) 触发或将函数绑定到被选元素的鼠标悬停事件


**jQuery的效果**
(1) 隐藏、显示(参数可选)
hide(speed,callback),show(speed,callback) ,toggle(speed,callback)[方法来切换 hide() 和 show() 方法]

(2) 淡入淡出效果(前三个参数可选，后一个的前两个参数是必须的)
fadeIn(speed,callback) 用于淡入已隐藏的元素,
fadeOut(speed,callback),方法用于淡出可见元素
fadeToggle(speed,callback),可以在 fadeIn() 与 fadeOut() 方法之间进行切换
fadeTo(speed,opacity,callback),允许渐变为给定的不透明度（值介于 0 与 1 之间）

(3) 滑动  可使元素上下滑动（参数可选）
slideDown(speed,callback) 用于向下滑动元素
slideUp() 用于向上滑动元素
slideToggle() 可以在 slideDown() 与 slideUp() 方法之间进行切换

(4) 动画 创建自定义的动画
animate()  用于创建自定义动画
```
$(selector).animate({params},speed,callback);
```
必需的 params 参数定义形成动画的 CSS 属性,其他可选

(5) 停止动画  用于在动画或效果完成前对它们进行停止
stop()  适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画

(6) Callback函数  在当前动画 100% 完成之后执行

(7) Chaining 把动作/方法链接起来
Chaining 允许我们在一条语句中允许多个 jQuery 方法（在相同的元素上）
例：
`$("#p1").css("color","red").slideUp(2000).slideDown(2000);`

**jQuery HTML**
(1) 获得内容和属性
获得内容 - text()、html() 以及 val()
text() - 设置或返回所选元素的文本内容
html() - 设置或返回所选元素的内容（包括 HTML 标记）
val() - 设置或返回表单字段的值

获取属性 - attr()

(2)设置内容和属性
text() - 设置或返回所选元素的文本内容
html() - 设置或返回所选元素的内容（包括 HTML 标记）
val() - 设置或返回表单字段的值
attr() 用于设置/改变属性值

(3) 添加元素
四个 jQuery 方法
append() - 在被选元素的结尾插入内容
prepend() - 在被选元素的开头插入内容
after() - 在被选元素之后插入内容
before() - 在被选元素之前插入内容

(4) 删除元素(2个方法)
remove() - 删除被选元素（及其子元素）
empty() - 从被选元素中删除子元素

(5)  获取并设置 CSS 类
addClass() - 向被选元素添加一个或多个类
removeClass() - 从被选元素删除一个或多个类
toggleClass() - 对被选元素进行添加/删除类的切换操作
css() - 方法设置或返回被选元素的一个或多个样式属性

(6) 尺寸
width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）
height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）
innerWidth() 方法返回元素的宽度（包括内边距）
innerHeight() 方法返回元素的高度（包括内边距）
outerWidth() 方法返回元素的宽度（包括内边距和边框）
outerHeight() 方法返回元素的高度（包括内边距和边框）
outerWidth(true) 方法返回元素的宽度（包括内边距、边框和外边距）
outerHeight(true) 方法返回元素的高度（包括内边距、边框和外边距）

**jQuery遍历**
(1) 向上遍历 DOM 树
parent() 返回被选元素的直接父元素
parents() 返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)
parentsUntil() 返回介于两个给定元素之间的所有祖先元素

(2) 向下遍历 DOM 树
children() 返回被选元素的所有直接子元素,该方法只会向下一级对 DOM 树进行遍历.
find() 返回被选元素的后代元素，一路向下直到最后一个后代.

(3) DOM 树中遍历元素的同胞元素
siblings() 返回被选元素的所有同胞元素
next() 返回被选元素的下一个同胞元素
nextAll() 返回被选元素的所有跟随的同胞元素
nextUntil() 返回介于两个给定参数之间的所有跟随的同胞元素
prev()
prevAll()
prevUntil()

(4) 过滤
first() 返回被选元素的首个元素, 
last() 返回被选元素的最后一个元素
和 eq() 被选元素中带有指定索引号的元素；允许您基于其在一组元素中的位置来选择一个特定的元素
filter() 和 not()返回不匹配标准的所有元素； 允许您选取匹配或不匹配某项指定标准的元素。


**AJAX**
AJAX 是与服务器交换数据的艺术，它在不重载全部页面的情况下，实现了对部分网页的更新.
通过 jQuery AJAX 方法，您能够使用 HTTP Get 和 HTTP Post 从远程服务器上请求文本、HTML、
XML 或 JSON - 同时您能够把这些外部数据直接载入网页的被选元素中.

**AJAX load() 方法**
load(URL,data,callback) 方法从服务器加载数据，并把返回的数据放入被选元素中.
必需的 URL 参数规定您希望加载的 URL。
可选的 data 参数规定与请求一同发送的查询字符串键/值对集合。
可选的 callback 参数是 load() 方法完成后所执行的函数名称

    可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：
    responseTxt - 包含调用成功时的结果内容
    statusTXT - 包含调用的状态
    xhr - 包含 XMLHttpRequest 对象
    
**AJAX get() 和 post() 方法**
GET - 从指定的资源请求数据,GET 方法可能返回缓存数据
POST - 向指定的资源提交要处理的数据,POST 方法不会缓存数据，并且常用于连同请求一起发送数据

`$.get(URL,callback);`
必需的 URL 参数规定您希望请求的 URL。
可选的 callback(data,status)参数是请求成功后所执行的函数名。

`$.post(URL,data,callback);`
必需的 URL 参数规定您希望请求的 URL。
可选的 data 参数规定连同请求发送的数据。
可选的 callback 参数是请求成功后所执行的函数名。

jQuery.getJSON() 使用 HTTP GET 请求从服务器加载 JSON 编码数据。
 .load() 从服务器加载数据，然后把返回到 HTML 放入匹配元素。
jQuery.getScript() 使用 HTTP GET 请求从服务器加载 JavaScript 文件，然后执行该文件。


