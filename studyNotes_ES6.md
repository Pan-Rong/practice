# ES6学习笔记[ES6规范](https://www.ecma-international.org/ecma-262/6.0/index.html)
  
    ES6是ES5的升级，它们都是JS编程语言现今的最大更新。95年出现了JS语言。

## 1.语言上的新增

**(1) 变量let和const**

    两种新的方式来声明变量：let和const；它们的作用域是到块(即用花括号表示)，而不是函数，不会提升；而var会提升到
    全局作用域或本地作用域即整个函数作用域。
    
    在代码块中使用let和const声明变量，该变量会陷入暂时性死区，直到该变量的声明被处理；这种行为会阻止变量被访问，除非它们被声明了。
    
let和const的规则
    
    使用let声明的变量可以重新赋值，但是不能在同一作用域内重新声明
    
    使用const声明的变量必须赋初始值，但是不能在同一作用域内重新声明，也无法重新赋值。
    
**(2) 模板字面量**

    ES6引入了模板字面量(在ES6开发版本中叫“模板字符串”)，其本质上是包含嵌入式表达式的字符串字面量。
    
    模板字面量是用倒引号(``)表示，可以包含用${expression}表示的占位符，且将换行符当成字符串的一部分。
    
    模板字面量中的嵌入式表达式不仅仅可以用来引用变量。你可以在嵌入式表达式中进行运算、调用函数和使用循环。
    
**(3) 解构**
    
    在ES6中，可以使用解构从数组和对象中提取值并赋给独特的变量。
    
    解构：从Perl和Python等语言中获得灵感，使你能够指定要从赋值左侧上的数组或对象中提取的元素。
    例1 解构数组：
```
      const point = [10, 25, -34];
      const [x, y, z] = point;
      console.log(x, y, z);
      Prints: 10 25 -34
```
    上述中，方括号 [ ] 表示被解构的数组，x、y 和 z 表示要将数组中的值存储在其中的变量。注意，你不需要指定要从
    中提取值的索引，因为索引可以暗示出来。
      
    例2 解构对象
```
    const gemstone = {
    type: 'quartz',
    color: 'rose',
    karat: 21.29
    };
    const {type, color, karat} = gemstone;
    console.log(type, color, karat);
    Prints: quartz rose 21.29
```
    上述中，花括号 { } 表示被解构的对象，type、color 和 karat 表示要将对象中的属性存储到其中的变量。因为 gemstone
    具有 type 属性，值自动存储在 type 变量中。
 
 **(4) 对象字面量简写法**
 
    在删掉不必要重复代码中，ES6推出了新简写法，例：
    对象字面量简写法：
    用来初始化对象并向对象中添加方法，使用和所分配的变量名称相同的名称初始化对象，可重对象属性中删除该属性。
    
    对象中简写方法名称：
    对象中添加方法时，可以省掉function关键字
    
 **(5) 迭代**
   
    1.ES6中添加了一个新的可迭代接口，它允许我们自定义对象的迭代方式(即循环遍历方式)，
    2.ES6中新增了一个循环，即for...of..,专门遍历可迭代对象(即实现了这个新迭代接口的对象，如string，array，Map和Set)
    
    for...of循环(优势)
    循环访问任何可迭代的数据类型，和for...in相似，但可以忽略索引(代码最简)；
    且可随时停止或退出for...of循环；
    不用担心向对象中添加新属性，for...of循环只循环访问对象中的值。
     
**(6) 展开...运算符**
    
    ES6中新增了展开运算符(用三个连续的点...表示)，可将字面量对象展开为多个元素
    例1 展开集合：
```
    const primes = new Set([2, 3, 5, 7, 11, 13, 17, 19, 23, 29]);
    console.log(...primes);
    Prints: 2 3 5 7 11 13 17 19 23 29
```
    例2 结合数组：
```
    const fruits = ["apples", "bananas", "pears"];
    const vegetables = ["corn", "potatoes", "carrots"];
    //const produce = fruits.concat(vegetables);
    const produce = [...fruits,...vegetables];
    console.log(produce);
    Prints: ["apples", "bananas", "pears", "corn", "potatoes", "carrots"]
```

**(7) 剩余参数**

    ES6中新增的另一个运算符，剩余参数也用三个连续点...表示，使你能够将不定数量的元素表示为数组。
    例1、将变量赋数组值时：
```
    const order = [20.17, 18.67, 1.50, "cheese", "eggs", "milk", "bread"];
    const [total, subtotal, tax, ...items] = order;
    console.log(total, subtotal, tax, items);
    Prints: 20.17 18.67 1.5 ["cheese", "eggs", "milk", "bread"]
```
    例2、可变参数函数(即接受不定数量参数的函数)
    在此之前可使用参数对象(arguments),现在可以使用剩余参数：
```
    function sum(...nums) {
      let total = 0;  
      for(const num of nums) {
        total += num;
      }
      return total;
    }
```

## 2.函数新增

**(1) 箭头函数(箭头函数表达式)**
    
    ES6新增函数，箭头函数，例,转换数组中的大小写：
```
    const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
        name => name.toUpperCase()
    );
```
    将“普通”函数转换成箭头函数的步骤：
    1.删掉关键字 function
    2.删掉圆括号
    3.删掉左右花括号
    4.删掉关键字 return
    5.删掉分号
    6.在参数列表和函数主体之间添加一个箭头（=>）
    
箭头函数和普通函数的区别：
    
    普通函数可以是函数声明或函数表达式，但箭头函数始终是表达式；所以仅在表达式有效时才能使用箭头函数，如：
    1.存储在变量中
    2.当做参数传递给函数
    3.存储在对象的属性中
    
    参数列表出现在箭头函数的箭头(=>)前面，当只有一个参数时，可以直接写参数名；若有多个或零个，则需要用圆括号。
    当箭头函数的函数主体只有一个表达式时，在函数主体周围没有花括号；自动返回表达式
    当函数主体需多行代码时，需将函数主体放在花括号内，需要使用return语句来返回内容
    
"this"在普通函数和箭头函数中的使用
    
    在普通函数中，this取决于它的函数(或方法)是如何被调用的，例：
    1.新的对象(使用new调用)，则构造函数中的this的值是新的对象
    2.指定的对象(使用call或apply调用)
      注：call和apply的区别，call方法接受的是若干个参数的列表；而apply方法接受的是一个
          包含多个参数的数组。
    3.上下文对象(即点符号左边的对象)
    4.全局对象或undefined
      以上三种情况都不存在是，函数中的this的值是全局对象，在严格模式下是undefined
 
    在箭头函数中的this:
    箭头函数中，this的值基于函数周围的上下文，即this的值与函数外面的this的值一样
    
 **(2) 默认函数参数**   
  
    ES6中新的方式创建默认值，即默认函数参数；
    要创建默认参数，需要添加等号(=)以及当参数未提供时参数应该设为默认值，其可以为任何
    JS数据类型
    
    当默认函数参数和解构一起使用时，战斗力提升好几倍~
    例：
```
    function createGrid([width = 5, height = 5] = []) {
      return `Generating a grid of ${width} by ${height}`;
    }
    createGrid(); // Generates a 5 x 5 grid
    Returns: Generates a 5 x 5 grid
```

**(3) JS中的类**

    JS不是基于类的语言，它使用函数来创建对象，并通过原型将它们关联在一起。所谓的JS类本质上还是一样的。
    
    ES5中的类
    1.构造函数使用new关键字被调用
    2.按照惯例，构造函数名以大写字母开头
    3.构造函数控制将被创建的对象的数据的设置
    4.“继承”的方法被放在构造函数的原型对象上
    
    ES6中类,新类的编写：(注：类里各函数之间不要逗号)
```
    class Plane {
      constructor(numEngines) {
        this.numEngines = numEngines;
        this.enginesActive = false;
       }
        startEngines() {
          console.log('starting engines…');
          this.enginesActive = true;
        }
    }
    //以下是ES5中的startEngines定义,且ES5中类定义没有构造器函数，像普通函数一样定义
    //Plane.prototype.startEngines = function () {
    //  console.log('starting engines...');
    //  this.enginesActive = true;
    //};
```  
    ES6中的子类
    在ES6中，使用super和extends关键字扩展类；
    关键字extends将自己设为子类，要让子类可以访问到父类，需要使用关键字super。
    super既可被用作函数，也可被用作对象，但是super必须在this之前被调用，例：
```
    class Tree {
        constructor(size = '10', leaves = {spring: 'green', summer: 'green', fall: 'orange', winter: null}) {
            this.size = size;
            this.leaves = leaves;
            this.leafColor = null;
        }   
        changeSeason(season) {
            this.leafColor = this.leaves[season];
            if (season === 'spring') {
            this.size += 1;
            }
          }
    }
    class Maple extends Tree {
        constructor(syrupQty = 15, size, leaves) {
            super(size, leaves);
            this.syrupQty = syrupQty;
        }
        changeSeason(season) {
            super.changeSeason(season);
            if (season === 'spring') {
                this.syrupQty += 1;
            }
        } 
        gatherSyrup() {
            this.syrupQty -= 3;
        }
    }
    
## 3.ES6新增内置功能
    
**(1) Symbol(标识符)**   

    Symbol 只是一个唯一标识符，最常用于唯一标识对象中的属性(如对象中属性的名字相同但value不同时).但是不能用来访问标识符本身。
    
    Symbol的创建：Symbol(),并添加一个可选的字符串作为其描述。例：
```
        const sym1 = Symbol('apple');
        console.log(sym1);//Symbol(apple)
```        

**(2) 迭代器协议和可迭代协议(不是ES6内置) **

    ES6中新增的两个协议：迭代器协议和可迭代协议
    
    其中，可迭代协议用来定义和自定义对象的迭代行为；工作原理：为了使对象可迭代，它必须实现可迭代接口(即必须包含默认的迭代器方法)。
    
    迭代器协议用来定义对象生成一系列值的标准方式；即定义对象如何迭代的流程。工作原理：通过执行.next() 方法来完成这一流程。next()
    方法是无参数函数，返回具有两个属性的对象：value(下个值数据)和done(为false继续迭代，为true达到末尾);
    
**(3) Set(集合、单值、ES6内置可迭代)**
  
    Set()数学意义上的集合，即每个数字都是唯一的，只出现一次；不基于索引，不可单独被访问.
    
    Set创建：new  Set();
    
    Set修改：.add()增加，.delete()删除，.clear()清除
    注：若增加时，条目重复，则Set中不增加(返回Set对象)；若删除时，条目没有，则不删除(成功返回true,失败返回false)
    
    Set使用：
      .size返回条目数；
      .has()检查Set中是否存在某个条目，若有返回true，没有返回false
      .values()返回Set中的SetIterator对象，即所有值；
      .keys()同.values()
      
    Set循环访问：
      1.使用SetIterator和.next()访问Set中的每一项
```
          const iterator = months.values();
          iterator.next();
```
      2.使用for...of循环
```
        const colors = new Set(['red', 'orange', 'yellow', 'green', 'blue', 'violet', 'brown', 'black']);
        for (const color of colors) {
             console.log(color);
        }    
```
    
**(4) WeakSet(弱集合)**    
 
    WeakSet和Set的区别：
      1.WeakSet只能包含对象；
      2.WeakSet无法迭代，不能循环访问
      3.WeakSet没有.clear()方法
    
    WeakSet创建：new WeakSet();
    
    垃圾回收：
    JS中创建新值会分配内存，当这些值不需要时，将自动释放内存。该过程就称为垃圾回收
    
    WeakSet 通过专门使用对象作为键值来利用这一点。如果将对象设为 null，则本质上是删除该对象，
    当 JS 的垃圾回收器运行时，该对象之前占用的内存将被释放，以便稍后在程序中使用。
   
**(5) Map(映射)**    
    Map是一个可以存储键值对的对象，键和值都可以是对象、原始值或二者的结合。
    
    Map创建：new Map();与Set不同，其不能通过值列表创建，要使用.set()方法添加键值。
          
    Map处理：
        .set()方法，有两个参数，第一个参数是键，用来引用第二个参数即值；
        .delete()方法移除键值对；
        .clear()清除所有键值对
      注：.set()方法添加已存在的，不会报错，但会覆盖；.delete()方法删除不存在的，不变；成功为true，失败为false
        .has()传入键来检查Map中是否存在该键值对
        .get()方法传入键，检查Map中的值
        .keys()&.values()将返回新的迭代器对象MapIterator
    
    Map循环访问：
      1.使用MapIterator和.next()循环访问每个键或值(取决于使用keys或values)
      2.使用for...of循环访问键值对
      3.使用Map的.forEach()访问
       
**(6) WeakMap(弱映射)**    

    WeakMap和Map的关键区别：
      1.WeakMap只能包含对象作为键，
      2.WeakMap无法迭代
      3.WeakMap没有.clear()方法
      
    WeakMap创建：new WeakMap()
    
    垃圾回收：(同WeakSet)
    
**(7) Promise**   

    promise 使你能够展开一些可以异步完成的工作，并回到常规工作
      
    Promise的创建：
        new Promise()；创建 promise 时，必须向其提供异步运行的代码(即带初始函数);
    Promise通过向初始函数中传入两个函数来提示请求成功或失败，通常我们将这两个函数称为resolve(成功)和reject(失败)
      
    Promise立即返回对象
    Promise将立即返回一个对象，该对象具有一个.then()方法，我们可以让该方法通知我们promise中的请求成功与否。
    .then()方法会接收两个函数：
      1.请求成功完成时要运行的函数
      2.请求失败时要运行的函数
        
**(8) Proxy**         

    让一个对象代表另一个对象，来处理另一个对象的所有交互。代理可以直接处理请求，接收或发送目标对象数据等。
      
    Proxy的创建：
      new Proxy()；Proxy构造函数接收两个项目：
        1.它将要代理的对象
        2.包含将为被代理对象处理的方法列表的对象(即处理器handler)
        例：
 ```
      ar richard = {status: 'looking for work'};
      var agent = new Proxy(richard, {});
      agent.status; // returns 'looking for work'
 ```

    handler对象中的Get Trap(捕获器)和Set Trap;trap是一种函数，如果未定义trap,默认行为会被发送给目标对象
    1. Get Trap(捕获器)
      
        get 用来截获对属性的调用,它不会实际地输出属性！
```
          const richard = {status: 'looking for work'};
          const handler = {
                get(target, propName) {
                    console.log(target); // the `richard` object, not `handler` and not `agent`
                    console.log(propName); // the name of the property the proxy (`agent` in this case) is checking
                    return target[propName];//可在调用后输出返回的值
                }
           };
            const agent = new Proxy(richard, handler);
            agent.status; // logs out the richard object (not the agent object!) and the name of the property being 
                          //accessed (`status`)
```   
    2. set trap    
          
        set trap 用来截获将更改属性的代码
```
          const richard = {status: 'looking for work'};
          const handler = {
              set(target, propName, value) {
                  if (propName === 'payRate') { // if the pay is being set, take 15% as commission
                        value = value * 0.85;
                      }
                    target[propName] = value;
                }
            };
            const agent = new Proxy(richard, handler);
            agent.payRate = 1000; // set the actor's pay to $1,000
            agent.payRate;// $850 the actor's actual pay
```
    3. Proxy中有13种不同的捕获器 
        
    4. 和ES5种额Getter/Setter相比，
        Proxy种的get/set在初始化对象时，不需要针对每个属性使用 getter/setter 初始化对象.
          
**(9) 生成器(generator)**            
          
    生成器(generator)，可在暂停的函数。
     
    定义方法：在function后面加上*星号；
     
    调用：生成器被调用时，不会运行函数中的任何代码，而是创建和返回迭代器。该迭代器可以用来运行实际生成器的内部代码。
        调用.next()函数。
     
    在生成器中，出现了关键字yield。yield会导致生成器暂停下来；
    yield关键字放在要暂停的语句后面，并且迭代器会记住上次暂停的位置；
    若想用yield向外界生成数据，yield+数据；则每次暂停后会返回该数据
      
    将数据发送回生成器中，使用.next()方法；例：
```
      function* displayResponse() {
          const response = yield;//
          console.log(`Your response is "${response}"!`);
       }
      const iterator = displayResponse();
      iterator.next(); // starts running the generator function
      iterator.next('Hello Udacity Student'); // send data into the generator
      // the line above logs to the console: Your response is "Hello Udacity Student"!
```
## 4.专业开发者功能

主流浏览器的平台功能更新网址：

[Google Chrome]( https://www.chromestatus.com/features#ES6)

[Microsoft Edge](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/?q=ES6)

[Mozilla Firefox](https://platform-status.mozilla.org/)

[Safari( Webkit)](https://webkit.org/status/)

[EMCAScript兼容性表格](http://kangax.github.io/compat-table/es6/)

**[Polyfill](https://en.wikipedia.org/wiki/Polyfill)**[polyfill的HTML5样板文件团队](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)

    Polyfill是通过复制某些浏览器没有的原生功能，来修复这些缺失的JS文件；
    Ployfill(或polyfiller)是一段代码(或插件)，可提供本希望浏览器能原生提供的技术
    例：
```
      if (!String.prototype.startsWith) {//避免覆盖原生startsWith方法
          String.prototype.startsWith = function (searchString, position) {
              position = position || 0;
              return this.substr(position, searchString.length) === searchString;
          };
        }
```

**[Babel(JS转译器)](https://babeljs.io/)**

    Babel可以将ES6转换成ES5，也可以将JSX(JS扩展语言)转化成JS，并将 Flow 转换为JS.







