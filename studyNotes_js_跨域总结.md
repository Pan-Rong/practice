# 跨域总结[参考1](https://segmentfault.com/a/1190000011145364),[参考2](http://www.ruanyifeng.com/blog/2016/04/cors.html),[参考3](github.com/Nealyang/YOU-SHOULD-KNOW-JS/blob/master/doc/basic_js/JavaScript中的跨域总结.md)

## 跨域

    跨域是指一个域下的文档或脚本试图去请求另一个域下的资源，这里跨越是广义的。
    
广义跨域：

    (1)资源跳转：A链接、重定向、表单提交
    (2)资源嵌入：<link>、<script>、<img>、<frame>等dom标签，还有样式中background:url()、@font-face()等文件外链；
    (3)脚本请求：js发起的ajax请求、dom和js对象的跨域操作等
    

我们常说的跨越是狭义的，是浏览器执行其他网站的脚本，是由浏览器同源策略限制的一类请求场景。

***同源策略***

     同源策略即：协议+域名+端口，三者相同，即便两个不同的域名指向同一个IP地址，也非同源(同一域名，不同文件或路径可以)。
     
同源策略限制以下几种行为：

     (1)Cookie、LocalStorage和IndexDB无法读取
     (2)DOM和JS对象无法获得
     (3)AJAX请求不能发送
   
## 跨越解决方案

     (1) 通过jsonp跨越
     (2) document.domain+iframe跨域
     (3) location.hash+iframe
     (4) window.name+iframe跨越
     (5) postMessage跨域
     (6) 跨域资源共享(cors)
     (7) nginx代理跨域
     (8) nodejs中间件代理跨域
     (9) WebSocket协议跨域
     
**(1) 通过jsonp跨域**

      通常为了减轻web服务器的负载，我们把js、css、img等静态资源分离到另一台独立域名的服务器上，
      在html页面中再通过相应的标签从不同域名下加载静态资源，而被浏览器允许，基于此原理，我们可
      以通过动态创建script，再请求一个带参网址实现跨域通信。
      
 1) 原生实现：
```
 <script>
     var script = document.createElement('script');
         script.type = 'text/javascript';
     // 传参并指定回调执行函数为onBack    
         script.src = 'http://www.domain2.com:8080/login?user=admin&callback=onBack';
         document.head.appendChild(script);//向head里添加script
      // 回调执行函数
     function onBack(res) {
            alert(JSON.stringify(res));
        }   
 </script>
```
 2) jQuery AJAX:
```
      $.ajax({
          url:'http://www.domain2.com:8080/login',
          type:'get',
          dataType:'jsonp',
          jsonpCallback:'onBack',
          data:{}//
      });
```
 3) vue js:(没用过，不是很懂)
```
     this.$http.jsonp('http://www.domain2.com:8080/login',{
          params:{},
          jsonp:'onBack'
     }).then((res)=>{
          console.log(res);
     })
```
 后端node.js代码示例：
```
      var querystring=require('querystring');
      var http=require('http');
      var server=http.createServer();
      server.on('request',function(req,res){
          var params=qs.parse(req.url.split('?')[1]); 
          var fn=params.callback;
          //jsonp返回设置
          res.writeHead(200,{'Content-Type':'text/javascript'});
          res.write(fn+'('+JSON.stringify(params)+')');
          res.end();
      });
      server.listen('8080');
      console.log('');
```
jsonp缺点：只能实现get一种请求

**(2) document.domain+iframe跨域**(目前不熟)
   
 此方案仅限主域相同，子域不同的跨域应用场景
 
 实现原理：两个页面都通过js强制设置document.domain为基础主域，就实现了同域。
 
 1) 父窗口：(http://www.domain.com/a.html)
```
    <iframe id="iframe" src="http://child.domain.com/b.html"></iframe>
    <script>
       document.domain = 'domain.com';
       var user = 'admin';
    </script>
```
 2) 子窗口：(http://child.domain.com/b.html) 
```
    <script>
        document.domain = 'domain.com';
        // 获取父窗口中变量
        alert('get js data from parent ---> ' + window.parent.user);
    </script>
```

**(3) location.hash+iframe跨域**(目前不熟)

 实现原理：a域与b域相互通信，通过中间页c来实现。三个页面，不同域之间利用iframe
 的location.hash传值，相同域之间直接js访问来通信。
 
      具体实现：A域：a.html->B域：b.html->A域：c.html，a与b不同域只能通过hash
      值单向通信，b与c也不同域也只能单向通信，但c与a同域，所以c可通过parent.parent
      访问a页面所有对象。(具体示例见参考链接)
  
**(4) window.name+iframe跨域** 
 
    window.name属性的独特之处：name值在不同的页面(甚至不同域名)加载后依旧存在，并且可以支持非常长的name值(2MB)
    
    总结：通过iframe的src属性由外域转向本地域，跨域数据即由iframe的window.name从外域传递到本地域。这个就巧妙地
         绕过了浏览器的跨域访问限制，但同时它又是安全操作。
    
         其实location.hash和window.name都是差不多的，都是利用全局对象属性的方法，然后这两种方法和jsonp也
         是一样的，就是只能够实现get请求。
         
**(5) postMessage跨域**

     postMessage是HTML5 XMLHttpRequest Level 2中的API，且是为数不多可以跨域操作的window属性之一，它可用于
     解决以下方面的问题：
     a) 页面和其打开的新窗口的数据传递；
     b) 多窗口之间消息传递
     c) 页面与嵌套的iframe消息传递
     d) 上面三个场景的跨域数据传递
     
     用法：postMessage(data,origin)方法接受两个参数
          data：  html5规范支持任意基本类型或可复制的对象，但部分浏览器只支持字符串，所以传参时最好用JSON.
                  stringify()序列化。
          origin：协议+主机+端口号，也可以设置为"*"，表示可以传递给任意窗口，如果要指定和当前窗口同源的话
                  设置为"/"。

**(6) 跨域资源共享(CORS)** 
 
 简介
 
    目前主流的跨域解决方案。CORS是一个W3C标准，它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了
    AJAx只能同源使用的限制。
    CORS需要浏览器和服务器同时支持，目前，所有浏览器都支持该功能。
 
    整个CORS通信过程，都是浏览器自动完成，不需要用户参与。对于开发者来说，CORS通信与同源的AJAX通信没有差别，
    代码完全一样。浏览器一旦发现AJAX请求跨源，就会自动添加一些附加的头信息，有时还会多出一次附加的请求，但用
    户不会有感觉。
 
    因此，实现CORS通信的关键是服务器。只要服务器实现了CORS接口，就可以跨源通信。
 
 两种请求
 
    一种是简单请求，另一种是非简单请求。只要满足下面条件就是简单请求：
    1) 请求方式为HEAD、POST 或者 GET
    2) http头信息不超出一下字段：Accept、Accept-Language 、 Content-Language、 Last-Event-ID、 
       Content-Type(限于三个值：application/x-www-form-urlencoded、multipart/form-data、text/plain)
    
    为什么要分为简单请求和非简单请求，因为浏览器对这两种请求方式的处理方式是不同的。
 
简单请求

基本流程

    对于简单请求，浏览器直接发出CORS请求。具体来说，就是在头信息之中，增加一个Origin字段。Origin字段用来说明，
    本次请求来自哪个源（协议 + 域名 + 端口）。服务器根据这个值，决定是否同意这次请求。
    
    如果Origin指定的源，不在许可范围内，服务器会返回一个正常的HTTP回应。浏览器发现，这个回应的头信息没有包含
    Access-Control-Allow-Origin字段（详见下文），就知道出错了，从而抛出一个错误，被XMLHttpRequest的
    onerror回调函数捕获。
 
    注意，这种错误无法通过状态码识别，因为HTTP回应的状态码有可能是200。
    
    有三个与CORS请求相关的字段，都以Access-Control-开头：
    1) Access-Control-Allow-Origin :该字段是必须的。它的值要么是请求时Origin字段的值，要么是一个*，表示接
       受任意域名的请求
    2) Access-Control-Allow-Credentials: 该字段可选。它的值是一个布尔值，表示是否允许发送Cookie.默认情况
       下，Cookie不包括在CORS请求之中。设为true，即表示服务器明确许可，Cookie可以包含在请求中，一起发给服务
       器。这个值也只能设为true，如果服务器不要浏览器发送Cookie，删除该字段即可。  
    3) Access-Control-Expose-Headers:该字段可选. CORS请求时，XMLHttpRequest对象的getResponseHeader()方
       法只能拿到6个基本字段:Cache-Control、Content-Language、Content-Type、Expires、Last-Modified、
       Pragma.如果想拿到其他字段，就必须在Access-Control-Expose-Headers里面指定。
       
withCredentials 属性

    上面说到，CORS请求默认不发送Cookie和HTTP认证信息。如果要把Cookie发到服务器，一方面要服务器同意，指定
    Access-Control-Allow-Credentials字段。
    
    另一方面，开发者必须在AJAX请求中打开withCredentials属性。
```
    var xhr = new XMLHttpRequest(); // IE8/9需用window.XDomainRequest兼容
        // 前端设置是否带cookie
        xhr.withCredentials = true;
        xhr.open('post', 'http://www.domain2.com:8080/login', true);
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
        xhr.send('user=admin');
        xhr.onreadystatechange = function() {
             if (xhr.readyState == 4 && xhr.status == 200) {
                 alert(xhr.responseText);
             }
        };
        // jquery
        $.ajax({
           ...
           xhrFields: {
              withCredentials: true // 前端设置是否带cookie
           },
           crossDomain: true, // 会让请求头中包含跨域的额外信息，但不会含cookie
            ...
         });
```
    否则，即使服务器同意发送Cookie，浏览器也不会发送。或者，服务器要求设置Cookie，浏览器也不会处理。
    但是，如果省略withCredentials设置，有的浏览器还是会一起发送Cookie。这时，可以显式关闭withCredentials。
    
    需要注意的是，如果要发送Cookie，Access-Control-Allow-Origin就不能设为星号，必须指定明确的、与请求网页一致的域名。
    同时，Cookie依然遵循同源政策，只有用服务器域名设置的Cookie才会上传，其他域名的Cookie并不会上传，且（跨
    源）原网页代码中的document.cookie也无法读取服务器域名下的Cookie。
    
非简单请求

    非简单请求是那种对服务器有特殊要求的请求，比如请求方法是PUT或DELETE，或者Content-Type字段的类型是application/json。
    
    非简单请求的CORS请求，会在正式通信之前，增加一次HTTP查询请求，称为"预检"请求（preflight）
    
    浏览器先询问服务器，当前网页所在的域名是否在服务器的许可名单之中，以及可以使用哪些HTTP动词和头信息字段。只有得到肯定
    答复，浏览器才会发出正式的XMLHttpRequest请求，否则就报错。
```
     var url = 'http://api.alice.com/cors';
     var xhr = new XMLHttpRequest();
         xhr.open('PUT', url, true);
         xhr.setRequestHeader('X-Custom-Header', 'value');
         xhr.send();
```
    浏览器发现，这是一个非简单请求，就自动发出一个"预检"请求，要求服务器确认可以这样请求。
    
    "预检"请求用的请求方法是OPTIONS，表示这个请求是用来询问的。头信息里面，关键字段是Origin，表示请求来自哪个源。
        
    除了Origin字段，"预检"请求的头信息包括两个特殊字段。
    1) Access-Control-Request-Method：该字段是必须的，用来列出浏览器的CORS,请求会用到哪些HTTP方法，上例是PUT。
    2) Access-Control-Request-Headers：该字段是一个逗号分隔的字符串，指定浏览器CORS请求会额外发送的头信息字段.
       上例是X-Custom-Header.

 预检请求的回应
    
    服务器收到"预检"请求以后，检查了Origin、Access-Control-Request-Method和Access-Control-Request-Headers字
    段以后，确认允许跨源请求，就可以做出回应.
    
    如果浏览器否定了"预检"请求，会返回一个正常的HTTP回应，但是没有任何CORS相关的头信息字段。这时，浏览器就会认定，
    服务器不同意预检请求，因此触发一个错误，被XMLHttpRequest对象的onerror回调函数捕获。控制台会打印出如下的报错
    信息。
    
    服务器回应的其他CORS相关字段如下：
    1) Access-Control-Allow-Methods：该字段必需，它的值是逗号分隔的一个字符串，表明服务器支持的所有跨域请求的
       方法。注意，返回的是所有支持的方法，而不单是浏览器请求的那个方法。这是为了避免多次"预检"请求.
    2) Access-Control-Allow-Headers：如果浏览器请求包括Access-Control-Request-Headers字段，则
       Access-Control-Allow-Headers字段是必需的。它也是一个逗号分隔的字符串，表明服务器支持的所有头信息字段，
       不限于浏览器在"预检"中请求的字段。
    3) Access-Control-Allow-Credentials： 该字段与简单请求时的含义相同.
    4) Access-Control-Max-Age： 该字段可选，用来指定本次预检请求的有效期，单位为秒。上面结果中，有效期是20天
      （1728000秒），即允许缓存该条回应1728000秒（即20天），在此期间，不用发出另一条预检请求。
    
    浏览器正常请求回应
    
    一旦服务器通过了"预检"请求，以后每次浏览器正常的CORS请求，就都跟简单请求一样，会有一个Origin头信息字段。服
    务器的回应，也都会有一个Access-Control-Allow-Origin头信息字段。
    
    浏览器的正常CORS请求。上面头信息的Origin字段是浏览器自动添加的。下面是服务器正常的回应。
    
    Access-Control-Allow-Origin字段是每次回应都必定包含的.
    
JSONP和CORS对比

    CORS与JSONP的使用目的相同，但是比JSONP更强大。JSONP只支持GET请求，CORS支持所有类型的HTTP请求。JSONP的优势
    在于支持老式浏览器，以及可以向不支持CORS的网站请求数据。
    
**(7) nginx代理跨域**(不熟，下次补)

**(8) Nodejs中间件代理跨域**
    
    node中间件实现跨域代理，原理大致与nginx相同，都是通过启一个代理服务器，实现数据的转发，也可以通过设置
    cookieDomainRewrite参数修改响应头中cookie中域名，实现当前域的cookie写入，方便接口登录认证。
    
    利用node + express + http-proxy-middleware搭建一个proxy服务器
    
**(9) WebSocket协议跨域**    

    WebSocket protocol是HTML5一种新的协议。它实现了浏览器与服务器全双工通信，同时允许跨域通讯，是server
    push技术的一种很好的实现。
    
    原生WebSocket API使用起来不太方便，我们使用Socket.io，它很好地封装了webSocket接口，提供了更简单、
    灵活的接口，也对不支持webSocket的浏览器提供了向下兼容。
    
实际上，http规定了表单是浏览器对服务器请求数据的唯一方式。   
    
    
