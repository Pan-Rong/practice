# JS模块化 CMD和AMD[链接](http://blog.csdn.net/jackwen110200/article/details/52105493)

**JS中模块的几种表现形式**

    (1) 函数封装
        有特定功能的函数封装在一起，就可以作为一个模块。
        缺点：污染了全局变量，容易与其他模块发生变量名冲突，且模块内函数的关系可能不明确。
        
    (2) 对象
        把所有的模块成员封装在一个对象中，然后在引用,如object.fn()；
        优点：避免全局变量污染，要保证模块名唯一；
        缺点：可以修改模块内的变量值。
       
    (3) 立即执行函数
        通过立即执行函数，来达到隐藏细节的目的
        var myModule=(function(){})();
        优点：无法修改我们没有暴露出来的变量、函数
        
**CommonJS**

    CommonJS规范是由NodeJS发扬光大的，
  
    1、定义模块
      根据CommonJS规范，一个单独的文件就是一个模块。每个模块都是一个单独作用域。即，在该模块内部定义的变量，
      无法被其他模块读取，除非定义为global对象。
    
    2、模块输出
      模块只有一个出口，module.exports对象，我们需要把模块希望输出的内容放入该对象。
    
    3、加载模块
      加载模块使用require方法，该方法读取一个文件并执行，返回文件内部的module.exports对象。
    
    例：
```
      //模块定义 myModel.js
      var name = 'Byron';
      function printName(){
        console.log(name);
      }
      function printFullName(firstName){
        console.log(firstName + name);
      }
      module.exports = {
        printName: printName,
        printFullName: printFullName
      }
      //加载模块
      var nameModule = require('./myModel.js');
      nameModule.printName();
```
    不同的实现对require的路径要求不同，一般可以省略js扩展名，可以使用相对路径，
    也可以使用绝对路径，甚至可以省略路径直接使用模块名(前提是该模块是系统内置模块)
   
## AMD   
 
    AMD(Asynchronous Module Definition)即异步模块定义，它是一个在浏览器端模块化开发的规范。
  
    由于不是JS原生支持，使用AMD规范进行页面开发需要用到对应的库函数，RequireJS，实际上AMD是RequireJS在
    推广过程中对模块定义
 
    requireJS主要解决两个问题
  
    1、多个js文件可能有依赖关系，被依赖的文件需要早于依赖它的文件加载到浏览器
    2、js加载的时候浏览器会停止页面渲染，加载文件越多，页面失去响应时间越长
```
     // 定义模块 myModule.js
     define(['dependency'], function(){
        var name = 'Byron';
        function printName(){
            console.log(name);
        }
        return {
            printName: printName
        };
      });
     // 加载模块 
     require(['myModule'], function (my){
　     my.printName();
      }); 
```
**语法**  
    
    requireJS定义一个函数define，它是全局变量，用来定义模块
    define(id?,dependencies?,factory);
      1.id:可选参数，用来定义模块的标识，如果没有提供该参数，脚本文件名(去掉拓展名)
      2.dependencies:是一个当前模块依赖的模块名称数组
      3.factory：工厂方法，模块初始化要执行的函数或对象。如果为函数，它应该只被执行一次。如果是对象，
        次对象应该为模块的输出值。
        
    在页面上使用require函数加载模块：
    require([dependencies],function(){});     
    require()函数接受两个参数：
      1.第一个参数是一个数组，表示所依赖的模块
      2.第二个参数是一个回调函数，当前面指定的模块都加载成功后，它将被调用。加载的模块会以参数形式传入
        该函数，从而在回调函数内部就可以使用这些模块
        
    require()函数在加载依赖的函数的时候是异步加载的，这样浏览器不会失去响应，它指
    定的回调函数，只有前面的模块都加载成功后，才会运行，解决了依赖性的问题。
    
## CMD
 
    CMD(Common Module Definition)即通用模块定义，CMD规范是国内发展出来的，CMD有个浏览器的实现SeaJS,
    SeaJS要解决的问题和requireJS一样，只不过在模块定义方式和模块加载(或运行、解析)时，有所不同。
    
**语言**

    Sea.js推崇一个模块一个文件，遵循统一的写法
    define(id?,deps?,factory)
      1.一个文件一个模块，所以经常就用文件名作为模块id
      2.CMD推崇依赖就近，所以一般不在define的参数中写依赖，在factory中写
      3.factory是一个函数，有三个参数，function(require,exports,module)
        (1) require是一个方法，接受模块标识作为唯一参数，用来获取其他模块提供的接口：require(id)
        (2) exports是一个对象，用来向外提供模块接口
        (3) module是一个对象，上面存储了与当前模块相关联的一些属性和方法
        
      例：
```
      // 定义模块  myModule.js
      define(function(require, exports, module) {
          var $ = require('jquery.js')
          $('div').addClass('active');
      });
      // 加载模块
      seajs.use(['myModule.js'], function(my){
      });
```

## AMD与CMD区别

    最明显的区别就是在模块定义时对依赖的处理不同
    (1)AMD依赖前置，在定义模块的时候就要声明其依赖的模块
    (2)CMD就近依赖，只有在用到某个模块的时候再去require
    (3)对依赖模块的执行时机处理不同，
  
    很多人说requireJS是异步加载模块，SeaJS是同步加载模块，其实不准确？(待我确认)加载都是异步的，只不过
    AMD依赖前置，JS可以方便知道依赖模块是谁，立即加载；而CMD就近依赖，需要把模块变成字符串解析一遍才知
    道依赖了那些模块，而解析模块用的时间短到可以忽略。
  
    同样都是异步加载模块，AMD在加载模块完成后就会执行该模块，所有模块都加载执行后会进入require的回调函
    数，执行主逻辑，这样的效果就是依赖模块的执行顺序和书写顺序不一定一致。
  
    CMD加载完某个依赖模块后并不执行，只是下载而已，在所有依赖模块加载完成后进入主逻辑，遇到require语句
    的时候才执行对应的模块，这样模块的执行顺序和书写顺序是完全一致的。
